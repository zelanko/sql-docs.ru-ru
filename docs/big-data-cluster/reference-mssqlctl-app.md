---
title: Справка по mssqlctl приложений
titleSuffix: SQL Server big data clusters
description: Справочная статья по mssqlctl команд приложения.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b418f1ded8d9911143b431ae9793c467c4e26eb4
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860655"
---
# <a name="mssqlctl-app"></a>Приложение mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки для **приложения** команды в **mssqlctl** средство. Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md).

## <a id="commands"></a> Команды

|||
|---|---|
| [создание](#create) | Создайте приложение. |
| [удалить](#delete) | Для удаления приложения. |
| [описания](#describe) | Описание приложения. |
| [init](#init) | Kickstart новый скелет приложения. |
| [Список](#list) | Список приложений. |
| [run](#run) | Запустите приложение. |
| [update](#update) | Обновите приложение. |
| [template (шаблон)](reference-mssqlctl-app-template.md) | Шаблон команды. |

## <a id="create"></a> Создание приложения mssqlctl

Создайте приложение.

```
mssqlctl app create
   --assets
   --code
   --description
   --entrypoint
   --inputs
   --name
   --outputs
   --runtime
   --spec
   --version
   --yes
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--активы -** | Список файловых ресурсов дополнительное приложение для включения. |
| **--code - c** | Путь к файлу кода R или Python. |
| **— Описание -d** | Описание приложения. |
| **--entrypoint** |  |
| **--входных данных** | Схема входного параметра. |
| **--name - n** | Имя приложения. |
| **--выходные данные** | Схема параметров выходных данных. |
| **Среда выполнения--- r** | Среда выполнения приложения.  Допустимые значения: Mleap, Python, R, служб SSIS. |
| **--spec -s** | Путь к каталогу с файлом YAML спецификаций, описывающий приложение. |
| **--версии - v** | Версия приложения. |
| **--Да -y** | Не запрашивать подтверждение при создании приложения из файла spec.yaml CWD. |

### <a name="examples"></a>Примеры

Создайте новое приложение с помощью spec.yaml (рекомендуется).

```
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```

Создайте новые встроенные приложения Python, с использованием аргументов.

```
mssqlctl app create --name add --version v1 --inputs x=float, y=float --outputs result=float --runtime Python --code add.py  --init init.py
```

Создайте новые встроенные приложения R, используя аргументы.

```
mssqlctl app create --name add --version v1 --inputs x=numeric, y=numeric --outputs result=numeric --runtime R --code add.R  --init init.R
```

Создайте новые встроенные приложения R с дополнительным файлом активы должны быть включены.

```
mssqlctl app create --name add --version v1 --runtime R --code  add.R --assets file.RData,/path/to/more/files
```

## <a id="delete"></a> mssqlctl app delete

Для удаления приложения.

```
mssqlctl app delete
   --name
   --version
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя приложения. |
| **--версии - v** | Версия приложения. |

### <a name="examples"></a>Примеры

Удаление приложения по имени и версии.

```
mssqlctl app delete --name reduce --version v1
```

## <a id="describe"></a> mssqlctl app describe

Описание приложения.

```
mssqlctl app describe
   --name
   --spec
   --version
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя приложения. |
| **--spec -s** | Путь к каталогу с файлом YAML спецификаций, описывающий приложение. |
| **--версии - v** | Версия приложения. |

### <a name="examples"></a>Примеры

Описывают приложение.

```
mssqlctl app describe --name reduce --version v1
```

## <a id="init"></a> init mssqlctl приложения

Kickstart новый скелет приложения.

```
mssqlctl app init
   --destination
   --name
   --spec
   --template
   --url
   --version
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--назначения -d** | Где разместить скелет приложения. Значение по умолчанию — текущий рабочий каталог. |
| **--name - n** | Имя приложения. |
| **--spec -s** | Создайте просто spec.yaml приложения. |
| **--шаблон -t** | Имя шаблона. Для получения полного списка off имена поддерживаемых шаблонов запустите `mssqlctl app template list`. |
| **--URL-адрес -u** | Укажите расположение репозитория другой шаблон. Значение по умолчанию — https://github.com/Microsoft/sql-server-samples.git. |
| **--версии - v** | Версия приложения. |

### <a name="examples"></a>Примеры

Сформировать шаблон нового приложения `spec.yaml` только.

```
mssqlctl app init --spec
```

Сформировать шаблон нового R приложения скелет приложения на основе `r` шаблона.

```
mssqlctl app init --name reduce --template r
```

Сформировать шаблон нового Python приложения скелет приложения на основе `python` шаблона.

```
mssqlctl app init --name reduce --template python
```

Сформировать шаблон нового SSIS приложения скелет приложения на основе `ssis` шаблона.

```
mssqlctl app init --name reduce --template ssis
```

## <a id="list"></a> mssqlctl app list

Список приложений.

```
mssqlctl app list
   --name
   --version
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя приложения. |
| **--версии - v** | Версия приложения. |

### <a name="examples"></a>Примеры

Приложение списка по имени и версии.

```
mssqlctl app list --name reduce  --version v1
```

Список всех версий приложения по имени.

```
mssqlctl app list --name reduce
```

Список всех приложений.

```
mssqlctl app list
```

## <a id="run"></a> Запуск приложения mssqlctl

Запустите приложение.

```
mssqlctl app run
   --name
   --version
   --inputs
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--name - n** | Имя приложения. |
| **--версии - v** | Версия приложения. |
| **--входных данных** | Приложение входных параметров в CSV-ФАЙЛ `name=value` формат. |

### <a name="examples"></a>Примеры

Запустите приложение без входных параметров.

```
mssqlctl app run --name reduce --version v1
```

Запуск приложения с помощью один входной параметр.

```
mssqlctl app run --name reduce --version v1 --inputs x=10
```

Запустите приложение с несколькими входными параметрами.

```
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6
```

## <a id="update"></a> обновление приложения mssqlctl

Обновите приложение.

```
mssqlctl app update
   --spec
   --yes
```

### <a name="parameters"></a>Параметры

| Параметры | Описание |
|---|---|
| **--spec -s** | Путь к каталогу с файлом YAML спецификаций, описывающий приложение. |
| **--Да -y** | Не запрашивать подтверждение при обновлении приложения из файла spec.yaml CWD. |

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других **mssqlctl** команды, см. в разделе [mssqlctl ссылку](reference-mssqlctl.md). Дополнительные сведения об установке **mssqlctl** инструмент, см. в разделе [установить mssqlctl для управления кластерами больших данных SQL Server 2019](deploy-install-mssqlctl.md).