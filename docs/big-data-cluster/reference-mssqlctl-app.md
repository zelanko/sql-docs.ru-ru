---
title: Справочник по приложениям мссклктл
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам приложения мссклктл.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0df3e9ca007fb6546310236f4c23d1775687cc5
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388388"
---
# <a name="mssqlctl-app"></a>Приложение mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье содержится справочник по командам **приложения** в средстве **мссклктл** . Дополнительные сведения о других командах **мссклктл** см. в разделе [Справочник по мссклктл](reference-mssqlctl.md).

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[шаблон приложения мссклктл](reference-mssqlctl-app-template.md) | См.
[Инициализация приложения мссклктл](#mssqlctl-app-init) | Kickstart новая схема приложения.
[Создание приложения мссклктл](#mssqlctl-app-create) | Создать приложение.
[Обновление приложения мссклктл](#mssqlctl-app-update) | Обновление приложения.
[Список приложений мссклктл](#mssqlctl-app-list) | Вывод списка приложений.
[Удаление приложения мссклктл](#mssqlctl-app-delete) | Удаление приложения.
[Запуск приложения мссклктл](#mssqlctl-app-run) | Запустить приложение.
[Описание приложения мссклктл](#mssqlctl-app-describe) | Описание приложения.
## <a name="mssqlctl-app-init"></a>Инициализация приложения мссклктл
Помогает Kickstart новые схемы приложений и (или) файлы спецификаций на основе сред выполнения.
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>Примеры
Формирование шаблона только для `spec.yaml` нового приложения.
```bash
mssqlctl app init --spec
```
Формирование `r` шаблона нового каркаса приложения R на основе шаблонов.
```bash
mssqlctl app init --name reduce --template r
```
Сформировать `python` шаблон на основе новой каркаса приложения Python в зависимости от шаблона.
```bash
mssqlctl app init --name reduce --template python
```
Сформировать схему нового приложения SSIS на основе `ssis` шаблона.
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--spec -s`
Создайте только приложение Spec. YAML.
#### `--name -n`
Имя приложения.
#### `--version -v`
Версия приложения.
#### `--template -t`
Имя шаблона. Полный список поддерживаемых имен шаблонов для запуска`mssqlctl app template list`
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
## <a name="mssqlctl-app-create"></a>Создание приложения мссклктл
Создайте приложение.
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>Примеры
Создайте новое приложение из каталога, содержащего допустимую спецификацию развертывания Spec. YAML.
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
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
## <a name="mssqlctl-app-update"></a>Обновление приложения мссклктл
Обновление приложения.
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>Примеры
Обновление существующего приложения из каталога, содержащего допустимую спецификацию развертывания Spec. YAML.
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
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
## <a name="mssqlctl-app-list"></a>Список приложений мссклктл
Вывод списка приложений.,
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>Примеры
Список приложений по имени и версии.
```bash
mssqlctl app list --name reduce  --version v1
```
Вывод списка всех версий приложений по имени.
```bash
mssqlctl app list --name reduce
```
Вывод списка всех версий приложений по имени.
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
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="mssqlctl-app-delete"></a>Удаление приложения мссклктл
Удаление приложения.
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
Увеличьте уровень детализации ведения журнала, чтобы отобразить все журналы отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: JSON, jsonc, Table, TSV.  По умолчанию: JSON.
#### `--query -q`
Строка запроса JMESPath. Дополнительные [http://jmespath.org/](http://jmespath.org/]) сведения и примеры см. в разделе.
#### `--verbose`
Увеличение уровня детализации ведения журнала. Используйте параметр--Debug для полных журналов отладки.
## <a name="mssqlctl-app-run"></a>Запуск приложения мссклктл
Запустите приложение.
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>Примеры
Запуск приложения без входных параметров.
```bash
mssqlctl app run --name reduce --version v1
```
Запустите приложение с 1 входным параметром.
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
## <a name="mssqlctl-app-describe"></a>Описание приложения мссклктл
Опишите приложение.
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>Примеры
Опишите приложение.
```bash
mssqlctl app describe --name reduce --version v1    
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

Дополнительные сведения о других командах **мссклктл** см. в разделе [Справочник по мссклктл](reference-mssqlctl.md). Дополнительные сведения об установке средства **мссклктл** см. в [статье Установка мссклктл для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).