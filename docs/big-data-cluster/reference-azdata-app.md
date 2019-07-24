---
title: Справочник по приложениям аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам приложения аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 793edde26ebebf9e55c5751adbedf662142280de
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426284"
---
# <a name="azdata-app"></a>приложение аздата

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье содержится справочник по командам **приложения** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[шаблон приложения аздата](reference-azdata-app-template.md) | См.
[Инициализация приложения аздата](#azdata-app-init) | Kickstart новая схема приложения.
[Создание приложения аздата](#azdata-app-create) | Создать приложение.
[Обновление приложения аздата](#azdata-app-update) | Обновление приложения.
[Список приложений аздата](#azdata-app-list) | Вывод списка приложений.
[Удаление приложения аздата](#azdata-app-delete) | Удаление приложения.
[Запуск приложения аздата](#azdata-app-run) | Запустить приложение.
[Описание приложения аздата](#azdata-app-describe) | Описание приложения.
## <a name="azdata-app-init"></a>Инициализация приложения аздата
Помогает Kickstart новые схемы приложений и (или) файлы спецификаций на основе сред выполнения.
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>Примеры
Формирование шаблона только для `spec.yaml` нового приложения.
```bash
azdata app init --spec
```
Формирование `r` шаблона нового каркаса приложения R на основе шаблонов.
```bash
azdata app init --name reduce --template r
```
Сформировать `python` шаблон на основе новой каркаса приложения Python в зависимости от шаблона.
```bash
azdata app init --name reduce --template python
```
Сформировать схему нового приложения SSIS на основе `ssis` шаблона.
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Создайте только приложение Spec. YAML.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
#### `--template -t`
Имя шаблона. Полный список поддерживаемых имен шаблонов для запуска`azdata app template list`
#### `--destination -d`
Место размещения каркаса приложения. По умолчанию: текущий рабочий каталог.
#### `--url -u`
Укажите другое расположение репозитория шаблонов. Параметры https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-create"></a>Создание приложения аздата
Создайте приложение.
```bash
azdata app create --spec -s 
                  
```
### <a name="examples"></a>Примеры
Создайте новое приложение из каталога, содержащего допустимую спецификацию развертывания Spec. YAML.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--spec -s`
Путь к каталогу с файлом спецификации YAML, описывающим приложение.
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
## <a name="azdata-app-update"></a>Обновление приложения аздата
Обновление приложения.
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>Примеры
Обновление существующего приложения из каталога, содержащего допустимую спецификацию развертывания Spec. YAML.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Путь к каталогу с файлом спецификации YAML, описывающим приложение.
#### `--yes -y`
Не запрашивать подтверждение при обновлении приложения из файла Spec. YAML КВД.
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
## <a name="azdata-app-list"></a>Список приложений аздата
Вывод списка приложений.,
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>Примеры
Список приложений по имени и версии.
```bash
azdata app list --name reduce  --version v1
```
Вывод списка всех версий приложений по имени.
```bash
azdata app list --name reduce
```
Вывод списка всех версий приложений по имени.
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
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-app-delete"></a>Удаление приложения аздата
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
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="azdata-app-run"></a>Запуск приложения аздата
Запустите приложение.
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
Запустите приложение с 1 входным параметром.
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
Запустите приложение с несколькими входными параметрами.
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
Входные параметры приложения в формате `name=value` CSV.
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
## <a name="azdata-app-describe"></a>Описание приложения аздата
Опишите приложение.
```bash
azdata app describe [--spec -s] 
                    [--name -n]  
                    [--version -v]
```
### <a name="examples"></a>Примеры
Опишите приложение.
```bash
azdata app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Путь к каталогу с файлом спецификации YAML, описывающим приложение.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
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
