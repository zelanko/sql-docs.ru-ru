---
title: Справочник по azdata app
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata app.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ec7e461705138905713b803e2f0f96934044d971
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155295"
---
# <a name="azdata-app"></a>azdata app

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Эта статья содержит справочную статью по **аздата**. 

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
azdata app init 
```
### <a name="examples"></a>Примеры
Создание только файла `spec.yaml` приложения.
```bash
azdata app init --spec
```
Сформировать схему приложения R на основе `r` шаблона.
```bash
azdata app init --name reduce --template r
```
Формирование `python` шаблона нового каркаса приложения Python, основанного на шаблоне.
```bash
azdata app init --name reduce --template python
```
Сформировать схему приложения служб SSIS на основе `ssis` шаблона.
```bash
azdata app init --name reduce --template ssis            
```
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
azdata app create 
```
### <a name="examples"></a>Примеры
Создание приложения из каталога, содержащего допустимую спецификацию развертывания spec.yaml.
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
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
azdata app update 
```
### <a name="examples"></a>Примеры
Обновление существующего приложения из каталога с допустимым файлом спецификации приложения spec.yaml.
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
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
azdata app list 
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
azdata app delete 
```
### <a name="examples"></a>Примеры
Удаление приложения по имени и версии.
```bash
azdata app delete --name reduce --version v1    
```
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
azdata app run 
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
azdata app describe 
```
### <a name="examples"></a>Примеры
Описание приложения.
```bash
azdata app describe --name reduce --version v1    
```
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
