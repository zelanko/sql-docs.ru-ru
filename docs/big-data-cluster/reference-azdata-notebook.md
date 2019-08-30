---
title: Справочник по azdata notebook
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata notebook.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f147e2b4ec785c3723d09cac6eb3548511946780
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158239"
---
# <a name="azdata-notebook"></a>azdata notebook

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Эта статья содержит справочную статью по **аздата**. 

## <a name="commands"></a>Команды
|     |     |
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
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Просмотр записной книжки.  Отображаются все ячейки, если только не будет обнаружена ячейка с ошибкой в ее выходных данных.  В этом случае вывод останавливается.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>Обязательные параметры
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
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
```
### <a name="examples"></a>Примеры
Запуск записной книжки.
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь к записной книжке для запуска.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--output-path`
Путь к каталогу, используемый для выходных данных записной книжки.  Записная книжка с выходными данными и любые выводимые ею файлы создаются относительно этого каталога.
#### `--output-html`
Необязательный флаг, показывающий, следует ли дополнительно преобразовать выходную записную книжку в формат HTML.  Создает второй выходной файл.
#### `--arguments -a`
Необязательный список аргументов записной книжки, которые необходимо ввести в выполнение записной книжки.  Кодируется как словарь JSON.  Пример: "{" Name ":" value "," имя2 ":" value2 "}"
#### `--interactive -i`
Запуск записной книжки в интерактивном режиме.
#### `--clear -c`
В интерактивном режиме очистите консоль перед отрисовкой ячейки.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

- Дополнительные сведения об установке средства **azdata** см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
