---
title: Справочник по BDC аздата
titleSuffix: SQL Server big data clusters
description: Справочная статья по командам BDC аздата.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 488394cbf4b52a952ffc46ab2ec6c9a273466bd5
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426044"
---
# <a name="azdata-bdc"></a>аздата BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В следующей статье приведены ссылки на команды **BDC** в средстве **аздата** . Дополнительные сведения о других командах **аздата** см. в разделе [Справочник по аздата](reference-azdata.md).

## <a name="commands"></a>Команды

|     |     |
| --- | --- |
[Создание BDC аздата](#azdata-bdc-create) | Создание кластера больших данных.
[Удаление BDC аздата](#azdata-bdc-delete) | Удалите кластер больших данных.
[Конфигурация аздата BDC](reference-azdata-bdc-config.md) | Команды конфигурации.
[Конечная точка BDC аздата](reference-azdata-bdc-endpoint.md) | Команды конечной точки.
[состояние аздата BDC](reference-azdata-bdc-status.md) | Команды состояния.
[Отладка BDC аздата](reference-azdata-bdc-debug.md) | Команды отладки.
[элемент управления BDC аздата](reference-azdata-bdc-control.md) | Команды управления.
[пул BDC аздата](reference-azdata-bdc-pool.md) | Команды пула.
[HDFS BDC аздата](reference-azdata-bdc-hdfs.md) | Модуль HDFS предоставляет команды для доступа к файловой системе HDFS.
[аздата BDC Spark](reference-azdata-bdc-spark.md) | Команды Spark позволяют пользователю взаимодействовать с системой Spark, создавая сеансы, инструкции и пакеты и управляя ими.
## <a name="azdata-bdc-create"></a>Создание BDC аздата
Создание SQL Server кластера больших данных. в системе требуется конфигурация KUBE config, а также следующие переменные среды [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD ', ' MSSQL_SA_PASSWORD ', ' KNOX_PASSWORD '].
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>Примеры

Интерактивный процесс развертывания BDC. Вы получите запрос на ввод необходимых значений.

```bash
azdata bdc create
```

Развертывание BDC с аргументами.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
Развертывание BDC с указанным именем вместо имени по умолчанию в профиле.
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

Развертывание BDC с аргументами — не будет выводиться запрос, так как используется флаг--force.

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>Необязательные параметры
#### `--name -n`
Имя кластера больших данных, используемое для пространств имен kubernetes.
#### `--config-profile -c`
Профиль конфигурации кластера больших данных, используемый для развертывания кластера: ["AKS-dev-test", "кубеадм-dev-test", "minikube-dev-test"]
#### `--accept-eula -a`
Вы принимаете условия лицензии? [да/нет]. Если вы не хотите использовать этот аргумент, можно задать для переменной среды ACCEPT_EULA значение Yes. Условия лицензии для этого продукта можно просмотреть по адресу https://aka.ms/azdata-eula и https://go.microsoft.com/fwlink/?LinkId=2002534.
#### `--node-label -l`
Метка узла кластера больших данных, используемая для обозначения узлов, на которых следует выполнить развертывание.
#### `--force -f`
Принудительное создание, пользователь не будет получать запрос на ввод каких бы то ни было значений, и все проблемы будут напечатаны как часть stderr.
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
## <a name="azdata-bdc-delete"></a>Удаление BDC аздата
Удалите SQL Server кластер больших данных — конфигурация KUBE требуется в вашей системе вместе со следующими переменными среды [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD '].
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>Примеры
Удаление BDC, когда имя пользователя и пароль контроллера уже заданы в вашей системной среде.
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>Обязательные параметры
#### `--name -n`
Имя кластера больших данных, используемое для пространства имен kubernetes.
### <a name="optional-parameters"></a>Необязательные параметры
#### `--force -f`
Принудительное удаление кластера больших данных.
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
