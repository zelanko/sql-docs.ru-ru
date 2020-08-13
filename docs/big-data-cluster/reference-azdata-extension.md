---
title: Справочник по расширению azdata
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам расширения azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9e2585a77c3117df8514622728d0f09df93d7bc2
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243005"
---
# <a name="azdata-extension"></a>Расширение azdata

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В следующей статье приводятся справочные сведения по командам `sql` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды
| Команда | Описание |
| --- | --- |
[azdata extension add](#azdata-extension-add) | Добавление расширения.
[azdata extension remove](#azdata-extension-remove) | Удаление расширения.
[azdata extension list](#azdata-extension-list) | Вывод списка установленных расширений.
## <a name="azdata-extension-add"></a>azdata extension add
Добавление расширения.
```bash
azdata extension add --source -s 
                     [--index]  
                     
[--pip-proxy]  
                     
[--pip-extra-index-urls]  
                     
[--yes -y]
```
### <a name="examples"></a>Примеры
Добавление расширения из URL-адреса.
```bash
azdata extension add --source https://contoso.com/some_ext-0.0.1-py2.py3-none-any.whl
```
Добавление расширения с локального диска.
```bash
azdata extension add --source ~/some_ext-0.0.1-py2.py3-none-any.whl
```
Добавление расширения с локального диска и использование для зависимостей прокси-сервера pip.
```bash
azdata extension add --source ~/some_ext-0.0.1-py2.py3-none-any.whl --pip-proxy https://user:pass@proxy.server:8080
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--source -s`
Путь к модулю расширения на диске или URL-адрес расширения
### <a name="optional-parameters"></a>Необязательные параметры
#### `--index`
Базовый URL-адрес папки пакетов Python (по умолчанию https://pypi.org/simple). Адрес должен указывать на репозиторий, совместимый со стандартом PEP 503 (простой API-интерфейс репозитория) или локальный каталог в таком же формате.
#### `--pip-proxy`
Прокси-сервер для pip, используемый для зависимостей расширений, в формате [пользователь:пароль@]прокси-сервер:порт
#### `--pip-extra-index-urls`
Разделенный пробелами список дополнительных URL-адресов используемых каталогов пакетов. Адрес должен указывать на репозиторий, совместимый со стандартом PEP 503 (простой API-интерфейс репозитория) или локальный каталог в таком же формате.
#### `--yes -y`
Не запрашивать подтверждение.
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
## <a name="azdata-extension-remove"></a>azdata extension remove
Удаление расширения.
```bash
azdata extension remove --name -n 
                        [--yes -y]
```
### <a name="examples"></a>Примеры
Удаление расширения.
```bash
azdata extension remove --name some-ext
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--name -n`
Имя расширения
### <a name="optional-parameters"></a>Необязательные параметры
#### `--yes -y`
Не запрашивать подтверждение.
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
## <a name="azdata-extension-list"></a>azdata extension list
Вывод списка установленных расширений.
```bash
azdata extension list 
```
### <a name="examples"></a>Примеры
Вывод списка расширений.
```bash
azdata extension list
```
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

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
