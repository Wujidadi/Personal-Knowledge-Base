# MQL

> MetaQuotes Language，MetaTrader系列（MT4/MT5）的開發語言。

## 官方文件

[【官方】MQL5 快速上手](https://www.mql5.com/zh/articles/447)

## 測試程式碼

副檔名須為 `mq5`  
放到 `MQL5` 目錄下的 `Scripts` 資料夾內，然後用 IDE (MetaEditor) 編譯執行  
執行檔的副檔名應為 `ex5`
```cpp
/*
|----------------------------------------
| 測試程式 001
|----------------------------------------
*/

void OnStart()
{
    // PrintSelectedSymbols();

    CheckSymbolIsSynchronized("USDTWD");
}

void PrintSelectedSymbols()
{
    bool symbolIsSelected = true;
    int symbolTotal = SymbolsTotal(symbolIsSelected);
    string symbolName;
    for (int i = 0; i < symbolTotal; i++)
    {
        symbolName = SymbolName(i, symbolIsSelected);
        Print(i + 1, ". ", symbolName);
    }
}

void CheckSymbolIsSynchronized(string symbolName)
{
    bool symbolIsSynchronized = SymbolIsSynchronized(symbolName);
    Print("Is ", symbolName, " synchronized? ", symbolIsSynchronized);
}
```

## 圖表模板

[Wujidadi.tpl](/MQL/Wujidadi.tpl)  
放到 `MQL5` 目錄下的 `Profiles\Templates` 資料夾內

## 研讀進度

> 2022-05-02

[同步交易品種](https://www.mql5.com/zh/docs/marketinformation/symbolissynchronized)
