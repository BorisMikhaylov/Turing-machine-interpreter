# Turing-Machine-Interpreter

### Илья Малахов

#### Подзадача 1(описание синтаксиса)

[Описание](https://github.com/ilma4/fl-2022-hse-win/blob/e01076629e96570c8fe10e6fed653d520166deaa/Description/description.md )


#### Подзадача 2(поддержка в IDE)

[Описание + инструкция по запуску](https://github.com/ilma4/fl-2022-hse-win/blob/5cc05b228ac8f1ecf950d56541b1fcd6026c6454/VSCode-extension/README.md)

### Борис Михайлов



## Отчёты



### Малахов Илья

Выполнено:

* Придумал и описал грамматику для описания Машины Тьюринга
* Описал эту грамматику в формате [TextMate](https://macromates.com/manual/en/language_grammars) для подсветки синтаксиса в VSCode
* Реализовал language server, с функциями автодополнения и проверки кода.
* Использовал парсер Бориса в сервере для получения идентификаторов(применяется в автодополнеии) и ошибок в коде.

Процесс реализации:

Изучил требования основных сред разработки к плагину поддержки нового языка. Выбрал Visual Studio Code из-за простоты и полезных [примеров](https://github.com/microsoft/vscode-extension-samples). Изучил устройство и принцип работы Машины Тьюринга, придумал несложную для парсинга грамматику, позволяющую делать корректную подсветку синтаксиса без LST. Описал эту грамматику в формате TextMate для подсветки в VSCode. Реализовал простой language server, который использует для автодополнения и проверки кода парсер Бориса.

Сложности:

Основная сложность была в том, чтобы понять как именно нужно сделать. Находил гайды про то как сделать ту или иную функцию в отрыве друг от друга, но не всё сразу. Но когда собрал достаточно информации, просто объединил несколько примеров в один проект и переделал под свои задачи и грамматику. Также были проблемы с пакетным менеджером `npm`(зависал), проблему решил vpn.
