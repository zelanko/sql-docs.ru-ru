---
title: Настройка развертываний
titleSuffix: SQL Server big data clusters
description: Сведения о том, как настроить развертывание кластера больших данных с помощью файлов конфигурации.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cae2c216245fdb6483b3ad07a88b3517c38550bd
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470743"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Настройка параметров развертывания для кластеров больших данных

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Чтобы настроить файлы конфигурации развертывания кластера, можно использовать любой редактор формата JSON, например VSCode. Чтобы внести эти изменения в скрипты для автоматизации, используйте команду **azdata bdc config**. В этой статье описано, как настроить развертывания кластера больших данных, изменив файлы конфигурации развертывания. Она содержит примеры изменения конфигурации для различных сценариев. Дополнительные сведения об использовании файлов конфигурации используются в развертываниях, см. в [руководстве по развертыванию](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>предварительные требования

- [Установка azdata](deploy-install-azdata.md).

- В каждом из примеров в этом разделе предполагается, что вы создали копию одной из стандартных конфигураций. Дополнительные сведения см. в статье [Создание настраиваемой конфигурации](deployment-guidance.md#customconfig). Например, следующая команда создает каталог `custom`, содержащий два файла конфигурации развертывания JSON — **cluster.json** и **control.json**, основанных на конфигурации **aks-dev-test** по умолчанию.

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Изменение имени кластера

Имя кластера — это имя кластера больших данных и пространство имен Kubernetes, которое будет создано при развертывании. Оно указывается в следующей части файла конфигурации развертывания **cluster.json**.

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

Следующая команда отправляет пару "ключ — значение" в параметр **--json-values**, чтобы изменить имя кластера больших данных на **test-cluster**.

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Имя кластера больших данных должно содержать только строчные буквы и цифры, без пробелов. Все артефакты Kubernetes (контейнеры, pod, наборы с отслеживанием состояния, службы) для кластера будут созданы в пространстве имен с именем, соответствующим указанному имени кластера.

## <a id="ports"></a> Обновление портов конечной точки

Конечные точки определяются для контроллера в файле **control.json**, а для шлюза и главного экземпляра SQL Server — в соответствующих разделах файла **cluster.json**. В следующей части файла конфигурации **control.json** показаны определения конечных точек для контроллера.

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

В следующем примере используется встроенная JSON для изменения порта для конечной точки **контроллера**.

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Настройка реплик пула

Характеристики каждого пула, например пула носителей, определяются в файле конфигурации **cluster.json**. Например, в следующей части **cluster.json** показано определение пула носителей.

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

В пуле можно настроить несколько экземпляров, изменив значение **replicas** для каждого пула. В следующем примере используется встроенная JSON для изменения этих значений пулов носителей и данных на `10` и `4` соответственно.

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> Настройка хранилища

Вы также может изменить характеристики и класс хранилища, используемые для каждого пула. Следующий пример назначает пользовательский класс хранилища для пула носителей, а также изменяет размер утверждения постоянного тома для хранения данных на 100 ГБ. Сначала создайте файл patch.json, как описано ниже, включающий раздел *storage* в дополнение к *type* и *replicas*.

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

После этого можете использовать команду **azdata bdc config patch**, чтобы обновить файл конфигурации **cluster.json**.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> Файл конфигурации на основе **kubeadm-dev-test** не имеет определения хранилища для каждого пула, но при необходимости вы можете добавить его с помощью описанного выше процесса.

Дополнительные сведения о конфигурации хранилища см. в статье [Сохраняемость данных при использовании кластера больших данных SQL Server в Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Настройка пула носителей без Spark

Кроме того, можно настроить пулы носителей для работы без Spark и создать отдельный пул Spark. Это позволяет масштабировать вычислительные мощности Spark независимо от хранилища. Чтобы узнать, как настроить пул Spark, ознакомьтесь с [примером файла исправления JSON](#jsonpatch) в конце этой статьи.



По умолчанию параметр **includeSpark** для пула носителей имеет значение true, поэтому для внесения изменений необходимо добавить поле **includeSpark** в конфигурацию хранилища. В следующем файле исправления JSON показано, как сделать это.

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

## <a id="podplacement"></a> Настройка размещения pod с помощью меток Kubernetes

Вы можете управлять размещением pod на узлах Kubernetes, имеющих определенные ресурсы для удовлетворения различных типов требований к рабочей нагрузке. Например, может потребоваться убедиться, что объекты pod пула носителей размещаются на узлах с увеличенным объемом хранилища или главные экземпляры SQL Server размещаются на узлах с увеличенными ресурсами ЦП и памяти. В этом случае сначала вы создадите разнородный кластер Kubernetes с различными типами оборудования, а затем [назначите метки узлов](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) соответствующим образом. Во время развертывания кластера больших данных можно указать одинаковые метки на уровне пула в файле конфигурации развертывания кластера. После этого Kubernetes сопоставит объекты pod на узлах, соответствующих указанным меткам.

В следующем примере показано, как изменить пользовательский файл конфигурации, включив в него параметр метки узла для главного экземпляра SQL Server. Обратите внимание, что во встроенных конфигурациях отсутствует ключ *nodeLabel*, поэтому нужно либо изменить пользовательский файл конфигурации вручную, либо создать файл исправления и применить его к пользовательскому файлу конфигурации.

Создайте в текущем каталоге файл **patch.json** со следующим содержимым.

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

## <a id="jsonpatch"></a> Файлы исправлений JSON

Файлы исправлений JSON настраивают несколько параметров одновременно. Дополнительные сведения об исправлениях JSON см. в статьях [Исправления JSON в Python](https://github.com/stefankoegl/python-json-patch) и [JSONPath Online Evaluator](https://jsonpath.com/).

Следующий файл **patch.json** вносит следующие изменения.

- Обновляет порт отдельной конечной точки в **control.json**.
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

- Обновляет все конечные точки (**port** и **serviceType**) в **control.json**.
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

- Обновляет параметры хранилища контроллера в **control.json**. Эти параметры применимы ко всем компонентам кластера, если только они не переопределены на уровне пула.
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

- Обновляет имя класса хранилища в **control.json**.
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

- Обновляет параметры хранилища пула для пула носителей в **cluster.json**.
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

- Обновляет параметры Spark для пула носителей в **cluster.json**.
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

- Создает пул Spark с 2 экземплярами в **cluster.json**.
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
> Дополнительные сведения о структуре и способах изменения файла конфигурации развертывания см. в [справочнике по файлу конфигурации развертывания для кластеров больших данных](reference-deployment-config.md).

Используйте команды **azdata bdc config**, чтобы применить эти изменения в файле исправления JSON. В следующем примере файл **patch.json** применяется к целевому файлу конфигурации развертывания **custom/cluster.json**.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об использовании файлов конфигурации в развертываниях кластера больших данных см. в статье [Развертывание кластеров больших данных SQL Server в Kubernetes](deployment-guidance.md#configfile).
