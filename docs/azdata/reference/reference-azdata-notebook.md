---
title: Справочник по azdata notebook
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata notebook.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: dd3d46ece53f15b694b28083e36d5cb991e2b411
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358122"
---
# <a name="azdata-notebook"></a>azdata notebook

Применяется к [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

В следующей статье приводятся справочные сведения по командам **sql** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|Команда|Описание|
| --- | --- |
[azdata notebook view](#azdata-notebook-view) | Просмотр записной книжки.  Для этого параметра работа останавливается при первой ошибке выполнения в ячейке.
[azdata notebook run](#azdata-notebook-run) | Запуск записной книжки.  Прекращение выполнения при первой ошибке.
## <a name="azdata-notebook-view"></a>azdata notebook view
Эта команда может использовать файл записной книжки и преобразовать Markdown, код и выходные данные в цветовой формат терминала.
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>Примеры
Просмотр записной книжки.  Отображаются все ячейки.
```bash
azdata notebook view --path "/home/me/notebooks/demo_notebook.ipynb"
```
Просмотр записной книжки.  Отображаются все ячейки, если только не будет обнаружена ячейка с ошибкой в ее выходных данных.  В этом случае вывод останавливается.
```bash
azdata notebook view --path "/home/me/notebooks/demo_notebook.ipynb" --stop-on-error
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--path -p`
Путь к записной книжке для просмотра.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--continue-on-error -c`
Продолжение отображения дополнительных ячеек без учета ошибок ячеек, обнаруженных в выходных данных записной книжки.  Поведение по умолчанию: остановка при обнаружении ошибки.  Остановка упрощает просмотр первой ячейки, в которой обнаружена ошибка.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-notebook-run"></a>azdata notebook run
Эта команда создает временный каталог и выполняет заданную записную книжку в нем как в рабочем каталоге.
```bash
azdata notebook run --path -p 
                    [--output-path]  
                    
[--output-html]  
                    
[--arguments -a]  
                    
[--interactive -i]  
                    
[--clear -c]  
                    
[--timeout -t]
```
### <a name="examples"></a>Примеры
Запуск записной книжки.
```bash
azdata notebook run --path "/home/me/notebooks/demo_notebook.ipynb"
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--path -p`
Путь к записной книжке для запуска.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--output-path`
Путь к каталогу, используемый для выходных данных записной книжки.  Записная книжка с выходными данными и любые выводимые ею файлы создаются относительно этого каталога.
#### `--output-html`
Необязательный флаг, показывающий, следует ли дополнительно преобразовать выходную записную книжку в формат HTML.  Создает второй выходной файл.
#### `--arguments -a`
Необязательный список аргументов записной книжки для внедрения в выполнение записной книжки.  Кодируется как словарь JSON.  Пример: '{"имя":"значение", "имя2":"значение2"}'
#### `--interactive -i`
Запустите записную книжку в интерактивном режиме.
#### `--clear -c`
В интерактивном режиме очистите консоль перед отображением ячейки.
#### `--timeout -t`
Подождите несколько секунд, пока завершится выполнение. Значение -1 означает бесконечное ожидание.
`600`
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

Дополнительные сведения об установке средства **azdata** см. в разделе [Установка azdata](..\install\deploy-install-azdata.md).

