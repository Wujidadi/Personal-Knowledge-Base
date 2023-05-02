# 自訂命令行工具

設定 Git ignore 以避免測試命令行被加入版控，  
並將樣式輸出的程式碼拆分到 trait 中，使測試命令行程式本體保持清潔。  
所有的測試命令行檔案都以 `Test` 開頭，以下範例為 `TestCmd`。  
注意以下程式碼中使用了自訂的 `JsonFlag` 常數物件（有程式碼）。

## app/Console/Commands/.gitignore

```gitignore
Test*
```

## app/Constants/JsonFlag.php

```php
<?php

namespace App\Constants;

/**
 * JSON flag 常數
 */
class JsonFlag
{
    /**
     * JSON 不轉義，值 = `320`（`JSON_UNESCAPED_SLASHES | JSON_UNESCAPED_UNICODE`）
     *
     * @var int
     */
    public const UNESCAPED = JSON_UNESCAPED_SLASHES | JSON_UNESCAPED_UNICODE;

    /**
     * JSON 不轉義格式化，值 = `448`（`JSON_UNESCAPED_SLASHES | JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT`）
     *
     * @var int
     */
    public const PRETTY = JSON_UNESCAPED_SLASHES | JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT;
}
```

## app/Console/Trait/StyledCommand.php

```php
<?php

namespace App\Console\Trait;

use App\Constants\JsonFlag;
use Symfony\Component\Console\Formatter\OutputFormatterStyle;

trait StyledCommand
{
    /**
     * Custom color map.
     *
     * @var array<string, string>
     */
    protected const COLOR = [
        'Gold' => '#FFD700',
        'RoyalBlue' => '#4169E1',
    ];

    /**
     * Custom style list.
     *
     * @var array<string, array<string, string|array>>
     */
    protected const STYLE = [
        'gold-text' => [
            'foreground' => self::COLOR['Gold'],
        ],
        'blue-text' => [
            'foreground' => self::COLOR['RoyalBlue'],
            'background' => 'white',
            'options' => ['underscore'],
        ],
    ];

    /**
     * Register custom styles.
     *
     * @return void
     */
    protected function registerStyles(): void
    {
        foreach (self::STYLE as $name => $style) {
            $this->output->getFormatter()->setStyle(
                $name,
                new OutputFormatterStyle(
                    $style['foreground'] ?? null,
                    $style['background'] ?? null,
                    $style['options'] ?? []
                )
            );
        }
    }

    /**
     * Output style of the console command.
     *
     * @var string|null
     */
    protected ?string $outputStyle = null;

    /**
     * Set the output style of the console command.
     *
     * @param string $styleName
     * @return void
     */
    protected function setOutputStyle(string $styleName): void
    {
        $this->outputStyle = $styleName;
    }

    /**
     * Output the console command result with specified custom style.
     *
     * @param mixed $data
     * @param bool $json
     * @param bool $prettyJson
     * @return void
     */
    protected function export(mixed $data, bool $json = false, bool $prettyJson = true): void
    {
        switch (true) {
            case is_string($data):
            case is_integer($data):
            case is_float($data):
            case is_null($data):
                $this->line($data, $this->outputStyle);
                break;
            case is_bool($data):
                $this->line($data ? 'true' : 'false', $this->outputStyle);
                break;
            case is_array($data):
            case is_object($data):
            default:
                if ($json) {
                    $this->line(json_encode($data, $prettyJson ? JsonFlag::PRETTY : JsonFlag::UNESCAPED), $this->outputStyle);
                } else {
                    $this->line(var_export($data, true), $this->outputStyle);
                }
                break;
        }
    }
}
```

## app/Console/Commands/TestCmd.php

`handle()` 的 `try` 部分為範例

```php
<?php

namespace App\Console\Commands;

use App\Console\Trait\StyledCommand;
use Exception;
use Illuminate\Console\Command;
use Symfony\Component\Console\Command\Command as CommandBase;

class TestCmd extends Command
{
    use StyledCommand;

    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'dev:test';

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = 'Command line tool for testing during development';

    /**
     * Execute the console command.
     *
     * @return int
     */
    public function handle(): int
    {
        $this->registerStyles();
        $this->setOutputStyle('gold-text');

        try {
            $model = new \App\Models\Tokens();
            $data = $model->find('TSK');
            $this->export($data->playerSettings->toArray(), true);

            return CommandBase::SUCCESS;
        } catch (Exception $e) {
            $this->export([
                'status' => $e::class,
                'code' => $e->getCode(),
                'message' => $e->getMessage(),
                'trace' => $e->getTraceAsString(),
            ]);

            return CommandBase::FAILURE;
        }
    }
}
```
