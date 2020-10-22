---
title: Справочник по azdata arc dc
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata arc dc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6f4f9c414221bc6eab400416d6ea09e692031aa5
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358782"
---
# <a name="azdata-arc-dc"></a>azdata arc dc

Применяется к [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

В следующей статье приводятся справочные сведения по командам **sql** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|Команда|Описание|
| --- | --- |
[azdata arc dc create](#azdata-arc-dc-create) | Создание контроллера данных.
[azdata arc dc delete](#azdata-arc-dc-delete) | Удаление контроллера данных.
[azdata arc dc endpoint](reference-azdata-arc-dc-endpoint.md) | Команды конечной точки.
[azdata arc dc status](reference-azdata-arc-dc-status.md) | Команды состояния.
[azdata arc dc config](reference-azdata-arc-dc-config.md) | Команды настройки.
[azdata arc dc debug](reference-azdata-arc-dc-debug.md) | Команды отладки.
[azdata arc dc export](#azdata-arc-dc-export) | Экспорт метрик, журналов или сведений об использовании.
[azdata arc dc upload](#azdata-arc-dc-upload) | Отправка экспортированного файла данных.
## <a name="azdata-arc-dc-create"></a>azdata arc dc create
Создание контроллера данных. Необходимо иметь в системе файл kube config, а также переменные среды ['AZDATA_USERNAME', 'AZDATA_PASSWORD'].
```bash
azdata arc dc create --namespace -ns 
                     --name -n  
                     
--connectivity-mode  
                     
--resource-group -g  
                     
--location -l  
                     
--subscription -s  
                     
[--profile-name]  
                     
[--path -p]  
                     
[--storage-class -sc]
```
### <a name="examples"></a>Примеры
Развертывание контроллера данных.
```bash
azdata arc dc create
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--namespace -ns`
Пространство имен Kubernetes, в котором нужно развернуть контроллер данных. Если оно уже существует, то оно и будет использоваться. Если оно не существует, сначала будет предпринята попытка создать его.
#### `--name -n`
Имя контроллера данных.
#### `--connectivity-mode`
Подключения к Azure (прямые или непрямые), в которых должен работать контроллер данных.
#### `--resource-group -g`
Группа ресурсов Azure, в которой должен быть добавлен ресурс контроллера данных.
#### `--location -l`
Расположение Azure, в котором будут храниться метаданные контроллера данных (например, eastus — Восточная часть США).
#### `--subscription -s`
ИД подписки Azure, в которой должен быть добавлен ресурс контроллера данных.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--profile-name`
Имя существующего профиля конфигурации. Для отображения доступных вариантов выполните команду `azdata arc dc config list`. Возможны следующие варианты: ['azure-arc-aks-premium-storage', 'azure-arc-ake', 'azure-arc-openshift', 'azure-arc-gke', 'azure-arc-aks-default-storage', 'azure-arc-kubeadm', 'azure-arc-eks', 'azure-arc-azure-openshift', 'azure-arc-aks-hci'].
#### `--path -p`
Путь к каталогу, где содержится используемый настраиваемый профиль конфигурации. Чтобы создать настраиваемый профиль конфигурации, выполните команду `azdata arc dc config init`.
#### `--storage-class -sc`
Класс хранения, который будет использоваться всеми томами постоянного хранения данных и журналов, требуемыми для объектов pod контроллеров данных.
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
## <a name="azdata-arc-dc-delete"></a>azdata arc dc delete
Удаление контроллера данных. Необходимо иметь в системе файл kube config.
```bash
azdata arc dc delete --name -n 
                     --namespace -ns  
                     
[--force -f]
```
### <a name="examples"></a>Примеры
Развертывание контроллера данных.
```bash
azdata arc dc delete
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя контроллера данных.
#### `--namespace -ns`
Пространство имен Kubernetes, в котором существует контроллер данных.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Принудительное удаление контроллера данных.
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
## <a name="azdata-arc-dc-export"></a>azdata arc dc export
Экспорт метрик, журналов или сведений об использовании в файл.
```bash
azdata arc dc export --type -t 
                     --path -p  
                     
[--force -f]
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--type -t`
Тип экспортируемых данных. Это могут быть журналы, метрики и данные об использовании.
#### `--path -p`
Полный или относительный путь, включающий имя файла для экспорта.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Принудительное создание выходного файла. Перезаписывает существующий файл (при наличии) по тому же пути.
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
## <a name="azdata-arc-dc-upload"></a>azdata arc dc upload
Отправка файла данных, экспортируемого из контроллера данных в Azure.
```bash
azdata arc dc upload --path -p 
                     
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--path -p`
Полный или относительный путь, включающий имя файла для отправки.
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

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). 

Дополнительные сведения об установке средства **azdata** см. в разделе [Установка azdata](..\install\deploy-install-azdata.md).

