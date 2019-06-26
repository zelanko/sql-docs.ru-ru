---
title: mssqlctl hdfs reference
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команды hdfs.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9051c3630fce005572bc3b939ebef9ed8d111e07
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394216"
---
# <a name="mssqlctl-hdfs"></a>mssqlctl hdfs

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **hdfs** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[mssqlctl hdfs shell](#mssqlctl-hdfs-shell) | Оболочки HDFS — это оболочка простой интерактивной командой для файловой системы HDFS.
[mssqlctl hdfs ls](#mssqlctl-hdfs-ls) | Список состояний заданного файла или каталога.
[mssqlctl hdfs exists](#mssqlctl-hdfs-exists) | Определите, существует ли файл или каталог.  Возвращает значение True, если существует и False в противном случае.
[mssqlctl hdfs mkdir](#mssqlctl-hdfs-mkdir) | Создайте каталог по указанному пути.
[mssqlctl hdfs mv](#mssqlctl-hdfs-mv) | Переместите указанный файл или путь в указанное расположение.
[mssqlctl hdfs create](#mssqlctl-hdfs-create) | Создайте текстовый файл в указанном расположении.  Простое текстовое содержимое можно добавить с помощью параметра данных.
[mssqlctl hdfs read](#mssqlctl-hdfs-read) | Читать содержимое файла.  Смещение и длина в байтах являются необязательными.
[mssqlctl hdfs rm](#mssqlctl-hdfs-rm) | Удаление файла или каталога.
[mssqlctl hdfs rmr](#mssqlctl-hdfs-rmr) | Рекурсивно удалить файл или каталог.
[mssqlctl hdfs chmod](#mssqlctl-hdfs-chmod) | Измените разрешение для заданного файла или каталога.
[mssqlctl hdfs chown](#mssqlctl-hdfs-chown) | Измените владельца или группу из указанного файла.
## <a name="mssqlctl-hdfs-shell"></a>mssqlctl hdfs shell
Оболочки HDFS — это оболочка простой интерактивной командой для файловой системы HDFS.
```bash
mssqlctl hdfs shell 
```
### <a name="examples"></a>Примеры
Запустите оболочку.
```bash
mssqlctl hdfs shell
```
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-ls"></a>mssqlctl hdfs ls
Список состояний заданного файла или каталога.
```bash
mssqlctl hdfs ls --path -p 
                 
```
### <a name="examples"></a>Примеры
Отображение состояния
```bash
mssqlctl hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь к отображение состояния.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-exists"></a>mssqlctl hdfs exists
Определите, существует ли файл или каталог.  Возвращает значение True, если существует и False в противном случае.
```bash
mssqlctl hdfs exists --path -p 
                     
```
### <a name="examples"></a>Примеры
Убедитесь в существовании файла или каталога.
```bash
mssqlctl hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Путь для проверки наличия существовании.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-mkdir"></a>mssqlctl hdfs mkdir
Создайте каталог по указанному пути.
```bash
mssqlctl hdfs mkdir --path -p 
                    
```
### <a name="examples"></a>Примеры
Создание каталога.
```bash
mssqlctl hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя каталога для создания.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-mv"></a>mssqlctl hdfs mv
Переместите указанный файл или путь в указанное расположение.
```bash
mssqlctl hdfs mv --source-path -s 
                 --target-path -t
```
### <a name="examples"></a>Примеры
Переместите файл или каталог.
```bash
mssqlctl hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--source-path -s`
Каталог, чтобы поместить.
#### `--target-path -t`
Расположение для перемещения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-create"></a>Создание mssqlctl hdfs
Создайте текстовый файл в указанном расположении.  Простое текстовое содержимое можно добавить с помощью параметра данных.
```bash
mssqlctl hdfs create --path -p 
                     --data -d
```
### <a name="examples"></a>Примеры
Создайте файл.
```bash
mssqlctl hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя создаваемого файла.
#### `--data -d`
Содержимое файла.  Предназначен для простого текстового содержимого.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-read"></a>mssqlctl hdfs read
Читать содержимое файла.  Смещение и длина в байтах являются необязательными.
```bash
mssqlctl hdfs read --path -p 
                   --offset  
                   --length -l
```
### <a name="examples"></a>Примеры
Чтение файла.
```bash
mssqlctl hdfs read --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла для чтения.
#### `--offset`
Число байтов смещение в файл для чтения.
#### `--length -l`
Длина данных для чтения.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-rm"></a>mssqlctl hdfs rm
Удаление файла или каталога.
```bash
mssqlctl hdfs rm --path -p 
                 
```
### <a name="examples"></a>Примеры
Удаление файла или каталога.
```bash
mssqlctl hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла для удаления.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-rmr"></a>mssqlctl hdfs rmr
Рекурсивно удалить файл или каталог.
```bash
mssqlctl hdfs rmr --path -p 
                  
```
### <a name="examples"></a>Примеры
Рекурсивное удаление каталог.
```bash
mssqlctl hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла, чтобы удалить рекурсивно.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-chmod"></a>mssqlctl hdfs chmod
Измените разрешение для заданного файла или каталога.
```bash
mssqlctl hdfs chmod --path -p 
                    --permission
```
### <a name="examples"></a>Примеры
Измените разрешения файла или каталога.
```bash
mssqlctl hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла или каталога, чтобы задать разрешения на.
#### `--permission`
Октеты разрешение для задания.  Пример «775».
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.
## <a name="mssqlctl-hdfs-chown"></a>mssqlctl hdfs chown
Измените владельца или группу из указанного файла.
```bash
mssqlctl hdfs chown --path -p 
                    --owner  
                    --group -g
```
### <a name="examples"></a>Примеры
Измените владельца и группу.
```bash
mssqlctl hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Имя файла или каталога, чтобы изменить владельца.
#### `--owner`
Имя владельца присвоено значение.
#### `--group -g`
Имя группы присвоено значение.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Увеличьте уровень подробного ведения журнала для отображения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат выходных данных.  Допустимые значения: json, jsonc, table, tsv.  По умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. См. в разделе [ http://jmespath.org/ ](http://jmespath.org/]) Дополнительные сведения и примеры.
#### `--verbose`
Увеличьте уровень подробного ведения журнала. Используйте параметр--debug, чтобы получить полные журналы отладки.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).