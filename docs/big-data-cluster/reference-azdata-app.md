---
title: Справочник по azdata app
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata app.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 031d8283f14e06515394bb26aa94049a43b6b79f
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653220"
---
# <a name="azdata-app"></a>azdata app

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приводятся справочные сведения по командам **app** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata app template](reference-azdata-app-template.md) | Шаблоны.
[azdata app init](#azdata-app-init) | Быстрое создание основы нового приложения.
[azdata app create](#azdata-app-create) | Создание приложения.
[azdata app update](#azdata-app-update) | Обновление приложения.
[azdata app list](#azdata-app-list) | Вывод списка приложений.
[azdata app delete](#azdata-app-delete) | Удаление приложения.
[azdata app run](#azdata-app-run) | Выполнение приложения.
[azdata app describe](#azdata-app-describe) | Описание приложения.
## <a name="azdata-app-init"></a>azdata app init
Позволяет быстро создать основу нового приложения и файлы спецификаций на основе сред выполнения.
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>Примеры
Создание только файла `spec.yaml` приложения.
```bash
azdata app init --spec
```
Создание основы приложения R на основе шаблона `r`.
```bash
azdata app init --name reduce --template r
```
Создание основы приложения Python на основе шаблона `python`.
```bash
azdata app init --name reduce --template python
```
Создание основы приложения SSIS на основе шаблона `ssis`.
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Создание только файла spec.yaml приложения.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
#### `--template -t`
Имя шаблона. Чтобы получить полный список имен поддерживаемых шаблонов, выполните команду `azdata app template list`.
#### `--destination -d`
Место для размещения основы приложения. По умолчанию текущий рабочий каталог.
#### `--url -u`
Указание другого расположения репозитория шаблонов. По умолчанию: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-create"></a>azdata app create
Создание приложения.
```bash
azdata app create --spec -s 
                  
```
### <a name="examples"></a>Примеры
Создание приложения из каталога, содержащего допустимую спецификацию развертывания spec.yaml.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--spec -s`
Путь к каталогу с YAML-файлом спецификации, описывающим приложение.
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
## <a name="azdata-app-update"></a>azdata app update
Обновление приложения.
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>Примеры
Обновление существующего приложения из каталога с допустимым файлом спецификации приложения spec.yaml.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Путь к каталогу с YAML-файлом спецификации, описывающим приложение.
#### `--yes -y`
Не запрашивать подтверждение при обновлении приложения из файла spec.yaml CWD.
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
## <a name="azdata-app-list"></a>azdata app list
Вывод списка приложений.
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>Примеры
Вывод списка приложений по имени и версии.
```bash
azdata app list --name reduce  --version v1
```
Вывод списка всех версий приложения по имени.
```bash
azdata app list --name reduce
```
Вывод списка всех версий приложения по имени.
```bash
azdata app list
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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
## <a name="azdata-app-delete"></a>azdata app delete
Удаление приложения.
```bash
azdata app delete --name -n 
                  --version -v
```
### <a name="examples"></a>Примеры
Удаление приложения по имени и версии.
```bash
azdata app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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
## <a name="azdata-app-run"></a>azdata app run
Запуск приложения.
```bash
azdata app run --name -n 
               --version -v  
               [--inputs]
```
### <a name="examples"></a>Примеры
Запуск приложения без входных параметров.
```bash
azdata app run --name reduce --version v1
```
Запуск приложения с одним входным параметром.
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
Запуск приложения с несколькими входными параметрами.
```bash
azdata app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--inputs`
Входные параметры приложения в формате CSV `name=value`.
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
## <a name="azdata-app-describe"></a>azdata app describe
Описание приложения.
```bash
azdata app describe [--spec -s] 
                    [--name -n]  
                    [--version -v]
```
### <a name="examples"></a>Примеры
Описание приложения.
```bash
azdata app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Путь к каталогу с YAML-файлом спецификации, описывающим приложение.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в разделе [Установка [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]аздата для управления ](deploy-install-azdata.md).
