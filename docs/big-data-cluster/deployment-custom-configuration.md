---
title: Настройка развертываний
titleSuffix: SQL Server big data clusters
description: Узнайте, как настроить развертывание кластера больших данных с помощью файлов конфигурации.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7559ecf9c7b17ca21c088ed531a347f88e89ee2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419435"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Настройка параметров развертывания для кластеров больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Чтобы настроить файлы конфигурации развертывания кластера, можно использовать любой редактор формата JSON, например VSCode. Чтобы внести эти изменения в скрипты для целей автоматизации, используйте команду **аздата BDC config** . В этой статье описывается настройка развертываний кластера больших данных путем изменения файлов конфигурации развертывания. В нем приводятся примеры изменения конфигурации для различных сценариев. Дополнительные сведения о том, как файлы конфигурации используются в развертываниях, см. в [руководстве](deployment-guidance.md#configfile)по развертыванию.

## <a name="prerequisites"></a>Предварительные требования

- [Установите аздата](deploy-install-azdata.md).

- В каждом из примеров в этом разделе предполагается, что вы создали копию одной из стандартных конфигураций. Дополнительные сведения см. [в разделе Создание пользовательской конфигурации](deployment-guidance.md#customconfig). Например, следующая команда `custom` создает каталог с именем, который содержит два файла конфигурации развертывания JSON: **cluster. JSON** и **Control. JSON**на основе конфигурации **AKS-dev-test** по умолчанию:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a>Изменение имени кластера

Имя кластера — это имя кластера больших данных и пространство имен Kubernetes, которое будет создано при развертывании. Он указывается в следующей части файла конфигурации развертывания **cluster. JSON** :

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

Следующая команда отправляет пару "ключ-значение" в параметр " **--JSON-Values** ", чтобы изменить имя кластера больших данных на **Test-Cluster**:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Имя кластера больших данных должно содержать только строчные буквы и цифры, без пробелов. Все артефакты Kubernetes (контейнеры, модули Pod, наборы отслеживании, службы) для кластера будут созданы в пространстве имен с тем же именем, что и у указанного имени кластера.

## <a id="ports"></a>Обновление портов конечной точки

Конечные точки определяются для контроллера в **Control. JSON** , а также для основного экземпляра шлюза и SQL Server в соответствующих разделах в **cluster. JSON**. В следующей части файла конфигурации **Control. JSON** показаны определения конечных точек для контроллера:

```json
"endpoints": [
    {
        "name": "Controller",
        "serviceType": "LoadBalancer",
        "port": 30080
    },
    {
        "name": "ServiceProxy",
        "serviceType": "LoadBalancer",
        "port": 30777
    }
]
```

В следующем примере используется встроенный JSON для изменения порта для конечной точки **контроллера** :

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a>Настройка реплик пула

Характеристики каждого пула, например пула носителей, определяются в файле конфигурации **cluster. JSON** . Например, в следующей части **cluster. JSON** показано определение пула носителей:

```json
"pools": [
   {
       "metadata": {
           "kind": "Pool",
           "name": "default"
       },
       "spec": {
           "type": "Storage",
           "replicas": 2
       }
   }
]
```

Количество экземпляров в пуле можно настроить, изменив значение **реплик** для каждого пула. В следующем примере используется встроенный JSON для изменения этих значений хранилища и пулов данных на `10` и `4` соответственно:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a>Настройка хранилища

Также можно изменить класс хранения и характеристики, используемые для каждого пула. В следующем примере для пула носителей назначается пользовательский класс хранения, а также обновляется размер постоянного тома для хранения данных в размере 100 ГБ. Сначала создайте файл patch. JSON, как описано ниже, в дополнение  к *типу* и *репликам* .

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "storage":{
        "data":{
                "size": "100Gi",
                "className": "myStorageClass",
                "accessMode":"ReadWriteOnce"
                },
        "logs":{
                "size":"32Gi",
                "className":"myStorageClass",
                "accessMode":"ReadWriteOnce"
                }
                },
        "type":"Storage",
        "replicas":2
      }
    }
  ]
}
```

Затем можно использовать команду **аздата BDC config Patch** , чтобы обновить файл конфигурации **cluster. JSON** .
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> Файл конфигурации на основе **кубеадм-dev-test** не имеет определения хранилища для каждого пула, но при необходимости можно использовать описанный выше процесс.

Дополнительные сведения о конфигурации хранилища см. [в статье сохраняемость данных с помощью SQL Server кластера больших данных в Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a>Настройка пула носителей без Spark

Можно также настроить пулы носителей для работы без Spark и создать отдельный пул Spark. Это позволяет масштабировать энергию вычислений Spark независимо от хранилища. Чтобы узнать, как настроить пул Spark, ознакомьтесь с [примером файла исправления JSON](#jsonpatch) в конце этой статьи.



По умолчанию параметр **инклудеспарк** для пула носителей имеет значение true, поэтому для внесения изменений необходимо добавить поле **инклудеспарк** в конфигурацию хранилища. В следующем файле исправления JSON показано, как добавить это.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "type":"Storage",
        "replicas":2,
        "includeSpark":false
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

## <a id="podplacement"></a>Настройка размещения Pod с помощью меток Kubernetes

Вы можете управлять размещением Pod на узлах Kubernetes, имеющих определенные ресурсы, для удовлетворения различных типов требований к рабочей нагрузке. Например, может потребоваться убедиться, что модули памяти пула носителей размещаются на узлах с большим объемом хранилища, или SQL Server главные экземпляры размещаются на узлах, имеющих больше ресурсов ЦП и памяти. В этом случае вы сначала создадите разнородный кластер Kubernetes с различными типами оборудования, а затем назначите [Метки узлов](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) соответствующим образом. Во время развертывания кластера больших данных можно указать одинаковые метки на уровне пула в файле конфигурации развертывания кластера. Kubernetes позаботится о установка соответствияи модулей Pod на узлах, соответствующих указанным меткам.

В следующем примере показано, как изменить пользовательский файл конфигурации, включив в него параметр метки узла для SQL Server главного экземпляра. Обратите внимание, что в встроенных конфигурациях отсутствует ключ *ноделабел* , поэтому необходимо либо изменить пользовательский файл конфигурации вручную, либо создать файл исправления и применить его к пользовательскому файлу конфигурации.

Создайте файл с именем **patch. JSON** в текущем каталоге со следующим содержимым:

```json
{
  "patch": [
     {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
           "type": "Master",
         "replicas": 1,
         "hadrEnabled": false,
         "endpoints": [
            {
             "name": "Master",
             "serviceType": "NodePort",
             "port": 31433
            }
          ],
         "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a id="jsonpatch"></a>Файлы исправления JSON

Файлы исправлений JSON настраивают несколько параметров одновременно. Дополнительные сведения об исправлениях JSON см. [в разделе исправления JSON в Python](https://github.com/stefankoegl/python-json-patch) и в [интерактивном оценщике JSONPath](https://jsonpath.com/).

Следующий файл **patch. JSON** выполняет следующие изменения:

- Обновляет порт одной конечной точки в **Control. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.endpoints[?(@.name=='Controller')].port",
          "value": 30000
        }   
      ]
    }
    ```

- Обновляет все конечные точки (**порт** и **serviceType**) в **Control. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.endpoints",
          "value": [
        {
          "serviceType": "LoadBalancer",
          "port": 30001,
          "name": "Controller"
        },
        {
            "serviceType": "LoadBalancer",
            "port": 30778,
            "name": "ServiceProxy"
        }
          ]
        }
      ]
    }
    ```

- Обновляет параметры хранилища контроллера в **Control. JSON**. Эти параметры применимы ко всем компонентам кластера, если они не переопределены на уровне пула.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage",
          "value": {
          "data": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
        }   
      ]
    }
    ```

- Обновляет имя класса хранения в **Control. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage.data.className",
          "value": "managed-premium"
        }   
      ]
    }
    ```

- Обновляет параметры хранилища пула для пула носителей в **cluster. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
          "value": {
        "type":"Storage",
        "replicas":2,
        "storage":{
        "data":{
            "size": "100Gi",
            "className": "myStorageClass",
            "accessMode":"ReadWriteOnce"
            },
        "logs":{
            "size":"32Gi",
            "className":"myStorageClass",
            "accessMode":"ReadWriteOnce"
            }
            }
         }
        }
      ]
    }
    ```

- Обновляет параметры Spark для пула носителей в **cluster. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.pools[?(@.spec.type == 'Storage')].hadoop.spark",
          "value": {
        "driverMemory": "2g",
        "driverCores": 1,
        "executorInstances": 3,
        "executorCores": 1,
        "executorMemory": "1536m"
          }
        }   
      ]
    }
    ```

- Создает пул Spark с 2 экземплярами в **cluster. JSON**.
    ```json
    {
      "patch": [
        {
          "op": "add",
          "path": "spec.pools/-",
          "value":
          {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        },
        "hadoop": {
          "yarn": {
            "nodeManager": {
              "memory": 12288,
              "vcores": 6
            },
            "schedulerMax": {
              "memory": 12288,
              "vcores": 6
            },
            "capacityScheduler": {
              "maxAmPercent": 0.3
            }
          },
          "spark": {
            "driverMemory": "2g",
            "driverCores": 1,
            "executorInstances": 2,
            "executorMemory": "2g",
            "executorCores": 1
          }
        }
          }
        } 
      ]
    }
    ```



> [!TIP]
> Дополнительные сведения о структуре и параметрах для изменения файла конфигурации развертывания см. в разделе [Справочник по файлам конфигурации развертывания для кластеров больших данных](reference-deployment-config.md).

Используйте команды **конфигурации BDC аздата** , чтобы применить изменения в файле исправления JSON. В следующем примере файл **patch. JSON** применяется к целевому файлу конфигурации развертывания **Custom или Cluster. JSON**.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об использовании файлов конфигурации в развертываниях кластера больших данных см. в статье [развертывание SQL Server кластеров больших данных в Kubernetes](deployment-guidance.md#configfile).
