---
title: Справочник по azdata notebook
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata notebook.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a5b30abf0fc8df71a3d791e0bd3927ccbe1e81b1
ms.sourcegitcommit: 8689a1abea3e2b768cdf365143b9c229194010c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/03/2020
ms.locfileid: "89734124"
---
# <a name="azdata-notebook"></a>azdata notebook

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

В следующей статье приводятся справочные сведения по командам `notebook` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
| Команда | Описание |
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

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](../install/deploy-install-azdata.md).
