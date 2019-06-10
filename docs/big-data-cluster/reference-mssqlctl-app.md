---
title: Справка по mssqlctl приложений
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команд приложения.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 75ada3528ab287cf49f717f99efa2405e4aad1db
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800945"
---
# <a name="mssqlctl-app"></a>Приложение mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **приложения** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[Шаблон приложения mssqlctl](reference-mssqlctl-app-template.md) | шаблоны.
[init mssqlctl приложения](#mssqlctl-app-init) | Kickstart новый скелет приложения.
[Создание приложения mssqlctl](#mssqlctl-app-create) | Создайте приложение.
[обновление приложения mssqlctl](#mssqlctl-app-update) | Обновите приложение.
[Список приложений mssqlctl](#mssqlctl-app-list) | Список приложений.
[Удаление приложения mssqlctl](#mssqlctl-app-delete) | Для удаления приложения.
[Запуск приложения mssqlctl](#mssqlctl-app-run) | Запустите приложение.
[описания mssqlctl приложения](#mssqlctl-app-describe) | Описание приложения.
## <a name="mssqlctl-app-init"></a>init mssqlctl приложения
Поможет вам kickstart новый скелет приложения и/или спецификаций файлов в зависимости от среды выполнения.
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>Примеры
Сформировать шаблон нового приложения `spec.yaml` только.
```bash
mssqlctl app init --spec
```
Сформировать шаблон нового R приложения скелет приложения на основе `r` шаблона.
```bash
mssqlctl app init --name reduce --template r
```
Сформировать шаблон нового Python приложения скелет приложения на основе `python` шаблона.
```bash
mssqlctl app init --name reduce --template python
```
Сформировать шаблон нового SSIS приложения скелет приложения на основе `ssis` шаблона.
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Создайте просто spec.yaml приложения.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
#### `--template -t`
Имя шаблона. Полный список off имена поддерживаемых шаблонов параметров запуска `mssqlctl app template list`
#### `--destination -d`
Где разместить скелет приложения. Значение по умолчанию — текущий рабочий каталог.
#### `--url -u`
Укажите расположение репозитория другой шаблон. Значение по умолчанию: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="mssqlctl-app-create"></a>Создание приложения mssqlctl
Создание приложения.
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>Примеры
Создайте новое приложение из каталога, содержащий спецификацию допустимым spec.yaml развертывания.
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--spec -s`
Путь к каталогу с файлом YAML спецификаций, описывающий приложение.
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
## <a name="mssqlctl-app-update"></a>обновление приложения mssqlctl
Обновление приложения.
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>Примеры
Обновление существующего приложения из каталога, содержащий спецификацию допустимым spec.yaml развертывания.
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Путь к каталогу с файлом YAML спецификаций, описывающий приложение.
#### `--yes -y`
Не запрашивать подтверждение при обновлении приложения из файла spec.yaml CWD.
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
## <a name="mssqlctl-app-list"></a>Список приложений mssqlctl
Список приложений.,
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>Примеры
Приложение списка по имени и версии.
```bash
mssqlctl app list --name reduce  --version v1
```
Список всех версий приложения по имени.
```bash
mssqlctl app list --name reduce
```
Список всех версий приложения по имени.
```bash
mssqlctl app list
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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
## <a name="mssqlctl-app-delete"></a>Удаление приложения mssqlctl
Удалите приложение.
```bash
mssqlctl app delete --name -n 
                    --version -v
```
### <a name="examples"></a>Примеры
Удаление приложения по имени и версии.
```bash
mssqlctl app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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
## <a name="mssqlctl-app-run"></a>Запуск приложения mssqlctl
Запустите приложение.
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>Примеры
Запустите приложение без входных параметров.
```bash
mssqlctl app run --name reduce --version v1
```
Запуск приложения с помощью один входной параметр.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10
```
Запустите приложение с несколькими входными параметрами.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--inputs`
Приложение входных параметров в CSV-ФАЙЛ `name=value` формат.
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
## <a name="mssqlctl-app-describe"></a>описания mssqlctl приложения
Описание приложения.
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>Примеры
Описывают приложение.
```bash
mssqlctl app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Путь к каталогу с файлом YAML спецификаций, описывающий приложение.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).