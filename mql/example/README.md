# 測試程式碼

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
