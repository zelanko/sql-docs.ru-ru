---
title: Настройка развертываний
titleSuffix: SQL Server big data clusters
description: Сведения о том, как настроить развертывание кластера больших данных с помощью файлов конфигурации.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0b76b6645e6be35f04b1a83670a99e529dcb84d6
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70745443"
---
# <a name="configure-deployment-settings-for-cluster-resources-and-services"></a>Настройка параметров развертывания для ресурсов и служб кластера

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Начиная с предварительно определенного набора профилей конфигурации, встроенных в средство управления аздата, можно легко изменить параметры по умолчанию, чтобы они лучше соответствовали требованиям к рабочей нагрузке BDC. Начиная с версии-кандидата, структура файлов конфигурации была обновлена, чтобы обеспечить детальное обновление параметров для каждой службы ресурса. 

Можно также задать конфигурации уровня ресурсов или обновить конфигурации для всех служб в ресурсе. Ниже приведена сводка по структуре для **BDC. JSON**.

```json
{
    "apiVersion": "v1",
    "metadata": {
        "kind": "BigDataCluster",
        "name": "mssql-cluster"
    },
    "spec": {
        "resources": {
            "nmnode-0": {...
            },
            "sparkhead": {...
            },
            "zookeeper": {...
            },
            "gateway": {...
            },
            "appproxy": {...
            },
            "master": {...
            },
            "compute-0": {...
            },
            "data-0": {...
            },
            "storage-0": {...
        },
        "services": {
            "sql": {
                "resources": [
                    "master",
                    "compute-0",
                    "data-0",
                    "storage-0"
                ]
            },
            "hdfs": {
                "resources": [
                    "nmnode-0",
                    "zookeeper",
                    "storage-0",
                    "sparkhead"
                ],
                "settings": {...
            },
            "spark": {
                "resources": [
                    "sparkhead",
                    "storage-0"
                ],
                "settings": {...
            }
        }
    }
}
```

Для обновления конфигураций на уровне ресурсов, например экземпляров в пуле, необходимо обновить спецификацию ресурсов. Например, чтобы обновить число экземпляров в пуле вычислений, измените этот раздел в файле конфигурации **BDC. JSON** :
```json
"resources": {
    ...
    "compute-0": {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Compute",
            "replicas": 4
        }
    }
    ...
}
``` 

Аналогично изменению параметров отдельной службы в определенном ресурсе. Например, если вы хотите изменить параметры памяти Spark только для компонента Spark в пуле носителей, обновите ресурс **Storage-0** с помощью раздела **параметров** для службы **Spark** в файле конфигурации **BDC. JSON.** .
```json
"resources":{
    ...
     "storage-0": {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Storage",
            "replicas": 2,
            "settings": {
                "spark": {
                    "driverMemory": "2g",
                    "driverCores": "1",
                    "executorInstances": "3",
                    "executorMemory": "1536m",
                    "executorCores": "1"
                }
            }
        }
    }
    ...
}
```

Если вы хотите применить те же конфигурации для службы, связанной с несколькими ресурсами, обновите соответствующие **Параметры** в разделе " **службы** ". Например, если вы хотите задать одинаковые параметры для Spark в обоих пулах носителей и пулах Spark, обновите раздел **параметров** в разделе службы **Spark** в файле конфигурации **BDC. JSON** .

```json
"services": {
    ...
    "spark": {
        "resources": [
            "sparkhead",
            "storage-0"
        ],
        "settings": {
            "driverMemory": "2g",
            "driverCores": "1",
            "executorInstances": "3",
            "executorMemory": "1536m",
            "executorCores": "1"
        }
    }
    ...
}
```


Чтобы настроить файлы конфигурации развертывания кластера, можно использовать любой редактор формата JSON, например VSCode. Чтобы внести эти изменения в скрипты для автоматизации, используйте команду **azdata bdc config**. В этой статье описано, как настроить развертывания кластера больших данных, изменив файлы конфигурации развертывания. Она содержит примеры изменения конфигурации для различных сценариев. Дополнительные сведения об использовании файлов конфигурации используются в развертываниях, см. в [руководстве по развертыванию](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Предварительные требования

- [Установка azdata](deploy-install-azdata.md).

- В каждом из примеров в этом разделе предполагается, что вы создали копию одной из стандартных конфигураций. Дополнительные сведения см. в статье [Создание настраиваемой конфигурации](deployment-guidance.md#customconfig). Например, следующая команда `custom` создает каталог с именем, который содержит два файла конфигурации развертывания JSON, **BDC. JSON** и **Control. JSON**на основе конфигурации по умолчанию **AKS-dev-test** .

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Изменение имени кластера

Имя кластера — это имя кластера больших данных и пространство имен Kubernetes, которое будет создано при развертывании. Он указывается в следующей части файла конфигурации развертывания **BDC. JSON** :

```json
"metadata": {
    "kind": "BigDataCluster",
    "name": "mssql-cluster"
},
```

Следующая команда отправляет пару "ключ — значение" в параметр **--json-values**, чтобы изменить имя кластера больших данных на **test-cluster**.

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Имя кластера больших данных должно содержать только строчные буквы и цифры, без пробелов. Все артефакты Kubernetes (контейнеры, pod, наборы с отслеживанием состояния, службы) для кластера будут созданы в пространстве имен с именем, соответствующим указанному имени кластера.

## <a id="ports"></a> Обновление портов конечной точки

Конечные точки определяются для контроллера в файле **Control. JSON** , а также для основного экземпляра шлюза и SQL Server в соответствующих разделах в **BDC. JSON**. В следующей части файла конфигурации **control.json** показаны определения конечных точек для контроллера.

```json
{
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
}
```

В следующем примере используется встроенная JSON для изменения порта для конечной точки **контроллера**.

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Настройка реплик пула

Конфигурации каждого ресурса, например пула носителей, определяются в файле конфигурации **BDC. JSON** . Например, в следующей части файла **BDC. JSON** показано определение ресурса **Storage-0** :

```json
"storage-0": {
    "metadata": {
        "kind": "Pool",
        "name": "default"
    },
    "spec": {
        "type": "Storage",
        "replicas": 2,
        "settings": {
            "spark": {
                "driverMemory": "2g",
                "driverCores": "1",
                "executorInstances": "3",
                "executorMemory": "1536m",
                "executorCores": "1"
            }
        }
    }
}
```

В пуле можно настроить несколько экземпляров, изменив значение **replicas** для каждого пула. В следующем примере используется встроенная JSON для изменения этих значений пулов носителей и данных на `10` и `4` соответственно.

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.storage-0.spec.replicas=10"
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.data-0.spec.replicas=4"
```

## <a id="storage"></a> Настройка хранилища

Вы также может изменить характеристики и класс хранилища, используемые для каждого пула. В следующем примере пользовательский класс хранения назначается хранилищу и пулам данных, а также обновляется объем постоянного тома для хранения данных в 500 ГБ для HDFS (пул носителей) и 100 ГБ для пула данных. Сначала создайте файл patch.json, как описано ниже, включающий раздел *storage* в дополнение к *type* и *replicas*.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "500Gi",
            "className": "myHDFSStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myHDFSStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.data-0.spec",
      "value": {
        "type": "Data",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "100Gi",
            "className": "myDataStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myDataStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    }
  ]
}
```

Затем можно использовать команду **аздата BDC Configuration Patch** , чтобы обновить файл конфигурации **BDC. JSON** .
```bash
azdata bdc config patch --config-file custom/bdc.json --patch ./patch.json
```

> [!NOTE]
> Файл конфигурации на основе **kubeadm-dev-test** не имеет определения хранилища для каждого пула, но при необходимости вы можете добавить его с помощью описанного выше процесса.

Дополнительные сведения о конфигурации хранилища см. в статье [Сохраняемость данных при использовании кластера больших данных SQL Server в Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Настройка пула носителей без Spark

Кроме того, можно настроить пулы носителей для работы без Spark и создать отдельный пул Spark. Это позволяет масштабировать вычислительные мощности Spark независимо от хранилища. Чтобы узнать, как настроить пул Spark, ознакомьтесь с [примером файла исправления JSON](#jsonpatch) в конце этой статьи.


По умолчанию параметр **инклудеспарк** для ресурса пула носителей имеет значение true, поэтому для внесения изменений необходимо изменить поле **инклудеспарк** в конфигурации хранилища. Следующая команда показывает, как изменить это значение с помощью встроенного JSON.

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.storage-0.spec.settings.spark.includeSpark=false"
```

## <a id="podplacement"></a> Настройка размещения pod с помощью меток Kubernetes

Вы можете управлять размещением pod на узлах Kubernetes, имеющих определенные ресурсы для удовлетворения различных типов требований к рабочей нагрузке. Например, может потребоваться убедиться, что модули ресурсов пула носителей размещены на узлах с большим объемом хранилища, или SQL Server главные экземпляры размещаются на узлах, имеющих больше ресурсов ЦП и памяти. В этом случае сначала вы создадите разнородный кластер Kubernetes с различными типами оборудования, а затем [назначите метки узлов](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) соответствующим образом. Во время развертывания кластера больших данных можно указать одинаковые метки на уровне пула в файле конфигурации развертывания кластера. После этого Kubernetes сопоставит объекты pod на узлах, соответствующих указанным меткам. Конкретный ключ метки, который необходимо добавить к узлам в кластере kubernetes, — это **MSSQL-clusterd**. Значение этой метки может быть любой выбранной строкой.

В следующем примере показано, как изменить пользовательский файл конфигурации, включив в него параметр метки узла для SQL Server экземпляра мастера, пула вычислений, пула данных & пула носителей. В встроенных конфигурациях отсутствует ключ *ноделабел* , поэтому необходимо либо изменить пользовательский файл конфигурации вручную, либо создать файл исправления и применить его к пользовательскому файлу конфигурации. Модуль SQL Server главного экземпляра будет развернут на узле, который содержит метку **MSSQL-Clustered** со значением **BDC-Master**. Пулы вычислений и модули пулов данных будут развернуты на узлах, которые содержат метку **MSSQL-Clustered** со значением **BDC-SQL**. Модули хранения данных пула носителей будут развернуты на узлах, которые содержат метку **MSSQL-Clustered** со значением **BDC-Storage**.

Создайте в текущем каталоге файл **patch.json** со следующим содержимым.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.master.spec",
      "value": {
        "type": "Master",
        "replicas": 1,
        "endpoints": [
          {
            "name": "Master",
            "serviceType": "NodePort",
            "port": 31433
          }
        ],
        "settings": {
          "sql": {
            "hadr.enabled": "false"
          }
        },
        "nodeLabel": "bdc-master"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.compute-0.spec",
      "value": {
        "type": "Compute",
        "replicas": 1,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.data-0.spec",
      "value": {
        "type": "Data",
        "replicas": 2,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 3,
        "nodeLabel": "bdc-storage",
        "settings": {
          "spark": {
            "includeSpark": "true"
          }
        }
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
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

- Обновляет параметры хранилища пула для пула носителей в **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "100Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    }
  ]
}
```

- Обновляет параметры Spark для пула носителей в **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.services.spark.settings",
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

- Создает пул Spark с 2 экземплярами в **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "add",
      "path": "spec.resources.spark-0",
      "value": {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        }
      }
    },
    {
      "op": "add",
      "path": "spec.services.spark.resources/-",
      "value": "spark-0"
    },
    {
      "op": "add",
      "path": "spec.services.hdfs.resources/-",
      "value": "spark-0"
    },
    {
      "op": "add",
      "path": "spec.services.spark.settings",
      "value": {
        "DriverMemory": "2g",
        "DriverCores": "1",
        "ExecutorInstances": "2",
        "ExecutorMemory": "2g",
        "ExecutorCores": "1"
      }
    }
  ]
}
```

> [!TIP]
> Дополнительные сведения о структуре и способах изменения файла конфигурации развертывания см. в [справочнике по файлу конфигурации развертывания для кластеров больших данных](reference-deployment-config.md).

Используйте команды **azdata bdc config**, чтобы применить эти изменения в файле исправления JSON. В следующем примере файл **patch. JSON** применяется к целевому файлу конфигурации развертывания **Custom/BDC. JSON**.

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
```

## <a name="disable-elasticsearch-to-run-in-privileged-mode"></a>Отключение ElasticSearch для запуска в привилегированном режиме
По умолчанию контейнер ElasticSearch работает в режиме привилегий в кластере больших данных. Это позволяет убедиться, что во время инициализации контейнера у контейнера есть достаточные разрешения для обновления параметра на узле требуемыми, когда ElasticSearch обрабатывает больший объем журналов. Дополнительные сведения об этом разделе можно найти в [этой статье](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html). 

Чтобы отключить контейнер, запускающий ElasticSearch в привилегированном режиме, необходимо обновить раздел **Settings** в **элементе управления. JSON** и указать значение **VM. Max _map_count** равным **-1**. Ниже приведен пример того, как будет выглядеть этот раздел:
```json
"settings": {
    "ElasticSearch": {
        "vm.max_map_count": "-1"
      }
}
```

Можно вручную изменить файл **Control. JSON** и добавить приведенный выше раздел в **спецификацию**. также можно создать файл исправления **elasticsearch-patch. JSON** , как показано ниже, и использовать **аздата** CLI для исправления файла **config. JSON** :

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec",
      "value": {
        "docker": {
            "registry": "mcr.microsoft.com",
            "repository": "mssql/bdc",
            "imageTag": "2019-RC1-ubuntu",
            "imagePullPolicy": "Always"
        },
        "storage": {
            "data": {
                "className": "default",
                "accessMode": "ReadWriteOnce",
                "size": "15Gi"
            },
            "logs": {
                "className": "default",
                "accessMode": "ReadWriteOnce",
                "size": "10Gi"
            }
        },
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
        ],
        "settings": {
            "ElasticSearch": {
                "vm.max_map_count": "-1"
             }
        }
       }
    }
  ]
}
```

Выполните следующую команду, чтобы исправить файл конфигурации:
```
azdata bdc config patch --config-file control.json --patch-file elasticsearch-patch.json
```

> [!IMPORTANT]
> Рекомендуется вручную обновить параметр **max_map_count** вручную на каждом узле в кластере Kubernetes, как описано в [этой статье](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html).
## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об использовании файлов конфигурации в развертываниях кластера больших данных см. в разделе [развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md#configfile).
