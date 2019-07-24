---
title: Справочник HDFS BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам HDFS BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8e892c2d501902ef915a297440ae5a6ffda83bce
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426184"
---
# <a name="azdata-bdc-hdfs"></a>HDFS BDC аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье содержится справочник по командам **HDFS в BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[оболочка HDFS BDC аздата](#azdata-bdc-hdfs-shell) | Оболочка HDFS представляет собой простую интерактивную командную оболочку для файловой системы HDFS.
[аздата BDC HDFS](#azdata-bdc-hdfs-ls) | Перечисление состояния заданного файла или каталога.
[Существует HDFS BDC аздата](#azdata-bdc-hdfs-exists) | Определить, существует ли файл или каталог.  Возвращает значение true, если существует, и false в противном случае.
[аздата BDC HDFS mkdir](#azdata-bdc-hdfs-mkdir) | Создать каталог по указанному пути.
[аздата BDC HDFS МВ](#azdata-bdc-hdfs-mv) | Переместить указанный файл или путь в указанное расположение.
[Создание каталога BDC аздата](#azdata-bdc-hdfs-create) | Создать текстовый файл в указанном расположении.  С помощью параметра данных можно добавить простое текстовое содержимое.
[аздата BDC HDFS CAT](#azdata-bdc-hdfs-cat) | Чтение содержимого файла.  Смещение и длина в байтах являются необязательными параметрами.
[аздата BDC HDFS RM](#azdata-bdc-hdfs-rm) | Удаляет файл или каталог.
[аздата BDC РМР](#azdata-bdc-hdfs-rmr) | Рекурсивно удалить файл или каталог.
[аздата BDC HDFS (chmod)](#azdata-bdc-hdfs-chmod) | Изменение разрешения для указанного файла или каталога.
[аздата BDC човн](#azdata-bdc-hdfs-chown) | Изменение владельца или группы указанного файла.
[Подключение HDFS BDC аздата](reference-azdata-bdc-hdfs-mount.md) | Управление подключением удаленных хранилищ в HDFS.
## <a name="azdata-bdc-hdfs-shell"></a>оболочка HDFS BDC аздата
Оболочка HDFS представляет собой простую интерактивную командную оболочку для файловой системы HDFS.
```bash
azdata bdc hdfs shell 
```
### <a name="examples"></a>Примеры
Запустите оболочку.
```bash
azdata bdc hdfs shell
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-ls"></a>аздата BDC HDFS
Перечисление состояния заданного файла или каталога.
```bash
azdata bdc hdfs ls --path -p 
                   
```
### <a name="examples"></a>Примеры
Состояние списка
```bash
azdata bdc hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь к состоянию списка.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-exists"></a>Существует HDFS BDC аздата
Определить, существует ли файл или каталог.  Возвращает значение true, если существует, и false в противном случае.
```bash
azdata bdc hdfs exists --path -p 
                       
```
### <a name="examples"></a>Примеры
Проверка существования файла или каталога.
```bash
azdata bdc hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь для проверки существования.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-mkdir"></a>аздата BDC HDFS mkdir
Создать каталог по указанному пути.
```bash
azdata bdc hdfs mkdir --path -p 
                      
```
### <a name="examples"></a>Примеры
Создать каталог.
```bash
azdata bdc hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя создаваемого каталога.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-mv"></a>аздата BDC HDFS МВ
Переместить указанный файл или путь в указанное расположение.
```bash
azdata bdc hdfs mv --source-path -s 
                   --target-path -t
```
### <a name="examples"></a>Примеры
Переместить файл или каталог.
```bash
azdata bdc hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--source-path -s`
Перемещаемый каталог.
#### `--target-path -t`
Расположение для перемещения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-create"></a>Создание каталога BDC аздата
Создать текстовый файл в указанном расположении.  С помощью параметра данных можно добавить простое текстовое содержимое.
```bash
azdata bdc hdfs create --path -p 
                       --data -d
```
### <a name="examples"></a>Примеры
Создать файл.
```bash
azdata bdc hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя создаваемого файла.
#### `--data -d`
Содержимое файла.  Предназначен для простого текстового содержимого.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-cat"></a>аздата BDC HDFS CAT
Чтение содержимого файла.  Смещение и длина в байтах являются необязательными параметрами.
```bash
azdata bdc hdfs cat --path -p 
                    --offset  
                    --length -l
```
### <a name="examples"></a>Примеры
Чтение файла.
```bash
azdata bdc hdfs cat --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя считываемого файла.
#### `--offset`
Число байтов смещения в файле для чтения.
#### `--length -l`
Длина данных для чтения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-rm"></a>аздата BDC HDFS RM
Удаляет файл или каталог.
```bash
azdata bdc hdfs rm --path -p 
                   
```
### <a name="examples"></a>Примеры
Удаляет файл или каталог.
```bash
azdata bdc hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя удаляемого файла.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-rmr"></a>аздата BDC РМР
Рекурсивно удалить файл или каталог.
```bash
azdata bdc hdfs rmr --path -p 
                    
```
### <a name="examples"></a>Примеры
Рекурсивный каталог recurs.
```bash
azdata bdc hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла для рекурсивного удаления.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-chmod"></a>аздата BDC HDFS (chmod)
Изменение разрешения для указанного файла или каталога.
```bash
azdata bdc hdfs chmod --path -p 
                      --permission
```
### <a name="examples"></a>Примеры
Измените разрешение на доступ к файлу или каталогу.
```bash
azdata bdc hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла или каталога, для которого нужно задать разрешения.
#### `--permission`
Октеты разрешений для установки.  Пример "775".
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-bdc-hdfs-chown"></a>аздата BDC човн
Изменение владельца или группы указанного файла.
```bash
azdata bdc hdfs chown --path -p 
                      --owner  
                      --group -g
```
### <a name="examples"></a>Примеры
Измените владельца и группу.
```bash
azdata bdc hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла или каталога для изменения владельца.
#### `--owner`
Имя владельца, для которого устанавливается значение.
#### `--group -g`
Имя группы, которой нужно присвоить значение.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в [статье Установка аздата для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
