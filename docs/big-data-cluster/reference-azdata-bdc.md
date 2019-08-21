---
title: Справочник по azdata bdc
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам azdata bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 44b0f8daafec86714bb8161c1d30130eed3d480d
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653446"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приводятся справочные сведения по командам **bdc** в средстве **azdata**. Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md).

## <a name="commands"></a>Команды

|     |     |
| --- | --- |
[azdata bdc create](#azdata-bdc-create) | Создание кластера больших данных.
[azdata bdc delete](#azdata-bdc-delete) | Удаление кластера больших данных.
[azdata bdc config](reference-azdata-bdc-config.md) | Команды настройки.
[azdata bdc endpoint](reference-azdata-bdc-endpoint.md) | Команды конечной точки.
[azdata bdc status](reference-azdata-bdc-status.md) | Команды состояния.
[azdata bdc debug](reference-azdata-bdc-debug.md) | Команды отладки.
[azdata bdc control](reference-azdata-bdc-control.md) | Команды контроля.
[azdata bdc pool](reference-azdata-bdc-pool.md) | Команды пула.
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | Модуль HDFS предоставляет команды для доступа к файловой системе HDFS.
[azdata bdc spark](reference-azdata-bdc-spark.md) | Команды Spark позволяют пользователю взаимодействовать с системой Spark, создавая сеансы, инструкции и пакеты и управляя ими.
## <a name="azdata-bdc-create"></a>azdata bdc create
Создание кластера больших данных SQL Server. В системе должен быть файл kube config, а также следующие переменные среды: ["CONTROLLER_USERNAME", "CONTROLLER_PASSWORD", "MSSQL_SA_PASSWORD", "KNOX_PASSWORD"].
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
Профиль конфигурации кластера больших данных, используемый для развертывания кластера: ["aks-dev-test", "kubeadm-dev-test", "minikube-dev-test"]
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно присвоить переменной среды ACCEPT_EULA значение "yes". Условия лицензии для этого продукта можно просмотреть по адресу [https://go.microsoft.com/fwlink/?LinkId=2002534](https://go.microsoft.com/fwlink/?LinkId=2002534).
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.
## <a name="azdata-bdc-delete"></a>azdata bdc delete
Удаление кластера больших данных SQL Server. В системе должен быть файл kube config, а также следующие переменные среды: ["CONTROLLER_USERNAME", "CONTROLLER_PASSWORD"].
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Примеры
Удаление кластера больших данных с именем пользователя и паролем контроллера, заданными в системной переменной.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Обязательные параметры
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
Строка запроса JMESPath. Дополнительные сведения и примеры см. в разделе [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Повышение уровня детализации журнала. Чтобы включить полные журналы отладки, используйте параметр --debug.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о других командах **azdata** см. в [справочнике по azdata](reference-azdata.md). Дополнительные сведения об установке средства **аздата** см. в разделе [Установка [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]аздата для управления ](deploy-install-azdata.md).
