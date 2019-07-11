---
title: Используйте curl для загрузки данных в HDFS | Документация Майкрософт
titleSuffix: SQL Server big data clusters
description: Используйте curl для загрузки данных в HDFS в кластерах SQL Server 2019 больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 40907155c819e4a1c6f9117a3b345fa8376efeb2
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729013"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-big-data-clusters"></a>Используйте curl для загрузки данных в HDFS в кластерах больших данных в SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются способы использования **curl** для загрузки данных в HDFS в кластерах SQL Server 2019 больших данных (Предварительная версия).

## <a name="obtain-the-service-external-ip"></a>Получить внешний IP-адрес службы

WebHDFS запускается после завершения развертывания, и доступ к нему осуществляется через Knox. Конечная точка Knox предоставляется через службу Kubernetes, именуемую **шлюз svc-external**.  Чтобы создать необходимые WebHDFS URL-адрес для отправки или скачивания файлов, вам понадобится **шлюз svc-external** службы внешний IP-адрес и имя кластера больших данных. Вы можете получить **шлюз svc-external** службы внешний IP-адрес, выполнив следующую команду:

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` Здесь — имя кластера, который указан в файле конфигурации развертывания. Имя по умолчанию — `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Создать URL-адрес для доступа к WebHDFS

Теперь можно создать URL-адрес для доступа к WebHDFS следующим образом:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Пример:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Список файлов

Файл списка в разделе **hdfs: / / / airlinedata**, используйте следующую команду curl:

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Локальный файл помещается в HDFS

Чтобы поместить новый файл **test.csv** из локального каталога в каталог airlinedata, используйте следующую команду curl ( **Content-Type** параметр является обязательным):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Создайте каталог

Чтобы создать каталог **тестирования** под `hdfs:///`, используйте следующую команду:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о больших данных кластера SQL Server, см. в разделе [что такое большие данные кластера SQL Server?](big-data-cluster-overview.md).
