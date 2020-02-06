---
title: Справочник по azdata bdc
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d5d5cb5256f4a1b8389d882300a89f0ee0012a99
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74820983"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

В следующей статье приводятся справочные сведения по командам `bdc` в средстве `azdata`. Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md)

## <a name="commands"></a>Команды
|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Создание кластера больших данных.
[azdata bdc delete](#azdata-bdc-delete) | Удаление кластера больших данных.
[azdata bdc upgrade](#azdata-bdc-upgrade) | Обновление образов, развернутых в каждом контейнере в кластере больших данных SQL Server.
[azdata bdc config](reference-azdata-bdc-config.md) | Команды настройки.
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Команды конечной точки.
[azdata bdc debug](reference-azdata-bdc-debug.md) | Команды отладки.
[azdata bdc status](reference-azdata-bdc-status.md) | Команды состояния BDC.
[azdata bdc control](reference-azdata-bdc-control.md) | Команды службы контроля.
[azdata bdc sql](reference-azdata-bdc-sql.md) | Команды службы SQL.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Команды службы HDFS.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Команды службы Spark.
[azdata bdc gateway](reference-azdata-bdc-gateway.md) | Команды службы шлюза.
[azdata bdc app](reference-azdata-bdc-app.md) | Команды службы приложений.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Команды Spark позволяют пользователю взаимодействовать с системой Spark, создавая сеансы, инструкции и пакеты и управляя ими.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Модуль HDFS предоставляет команды для доступа к файловой системе HDFS.
## <a name="azdata-bdc-create"></a>azdata bdc create
Создание кластера больших данных SQL Server. В системе должна быть конфигурация Kubernetes, а также следующие переменные среды: ['AZDATA_USERNAME', 'AZDATA_PASSWORD'].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Примеры
Интерактивный процесс развертывания кластера больших данных — выводятся запросы требуемых значений.
```bash
azdata bdc create
```
Развертывание кластера больших данных с аргументами.
```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
Развертывание кластера больших данных с указанным именем вместо имени по умолчанию в профиле.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```
Развертывание кластера больших данных с аргументами; запросы не выводятся, так как используется флаг --force.
```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```
### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя кластера больших данных, используемого для пространств имен Kubernetes.
#### `--config-profile -c`
Профиль конфигурации кластера больших данных, используемый для развертывания кластера: ['kubeadm-dev-test', 'kubeadm-prod', 'aks-dev-test', 'aks-dev-test-ha']
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". С условиями лицензии для azdata можно ознакомиться по адресу https://aka.ms/eula-azdata-en. Условия лицензии для кластера больших данных: Enterprise°— https://go.microsoft.com/fwlink/?linkid=2104292, Standard°— https://go.microsoft.com/fwlink/?linkid=2104294, Developer°— https://go.microsoft.com/fwlink/?linkid=2104079.
#### `--node-label -l`
Метка узлов кластера больших данных, используемая для указания узлов, в которых будет выполняться развертывание.
#### `--force -f`
Принудительное создание; пользователь не будет получать запросы на ввод значений; все ошибки будут выводиться в рамках потока stderr.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Удаление кластера больших данных SQL Server. В системе должна быть конфигурация Kubernetes.
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Примеры
Удаление BDC.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--name -n`
Имя кластера больших данных, используемого для пространства имен Kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Принудительное удаление кластера больших данных.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-upgrade"></a>azdata bdc upgrade
Обновление образов, развернутых в каждом контейнере в кластере больших данных SQL Server. Обновленные образы создаются на основе переданного образа Docker. Если обновленные образы не из того же репозитория образов Docker, из которого образы, развернутые в текущий момент, то необходимо указать параметр "repository".
```bash
azdata bdc upgrade --name -n 
                   --tag -t  
                   [--repository -r]
```
### <a name="examples"></a>Примеры
Обновление BDC до нового образа с помощью тега "cu2" из того же репозитория.
```bash
azdata bdc upgrade -t cu2
```
Обновление BDC до новых образов с помощью тега "cu2" из нового репозитория "foo/bar/baz".
```bash
azdata bdc upgrade -t cu2 -r foo/bar/baz
```
### <a name="required-parameters"></a>Необходимые параметры
#### `--name -n`
Имя кластера больших данных, используемого для пространств имен Kubernetes.
#### `--tag -t`
Тег целевого образа Docker для обновления всех контейнеров в кластере.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--repository -r`
Репозиторий Docker, откуда все контейнеры в кластере должны получать свои образы.
### <a name="global-arguments"></a>Глобальные аргументы
#### `--debug`
Повышение уровня детализации журнала для включения всех журналов отладки.
#### `--help -h`
Отображение этого справочного сообщения и выход.
#### `--output -o`
Формат вывода.  Допустимые значения: json, jsonc, table, tsv.  Значение по умолчанию: json.
#### `--query -q`
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о других командах `azdata` см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства `azdata` см. в статье [Установка azdata для управления кластерами больших данных SQL Server 2019](deploy-install-azdata.md).
