---
title: Используйте curl для загрузки данных в HDFS в кластерах SQL Server 2019 больших данных | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 1a7c7691ec20f459f39a39270e9a78fc9d8ad96f
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017550"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-2019-big-data-clusters"></a>Используйте curl для загрузки данных в HDFS в кластерах SQL Server 2019 больших данных

В этой статье описываются способы использования **curl** для загрузки данных в HDFS в кластерах SQL Server 2019 больших данных (Предварительная версия).

## <a name="obtain-the-service-external-ip"></a>Получить внешний IP-адрес службы

WebHDFS запускается после завершения развертывания, и доступ к нему осуществляется через Knox. Конечная точка Knox предоставляется через службу Kubernetes, именуемую **безопасности конечных точек**.  Чтобы создать необходимые WebHDFS URL-адрес для отправки или скачивания файлов, вам понадобится **безопасности конечных точек** службы внешний IP-адрес и имя кластера. Вы можете получить **безопасности конечных точек** службы внешний IP-адрес, выполнив следующую команду:

```bash
kubectl get service endpoint-security -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<cluster name>` Здесь — имя кластера, который использовался при запуске `mssqlctl cluster create --name <cluster name>`.

## <a name="construct-the-url-to-access-webhdfs"></a>Создать URL-адрес для доступа к WebHDFS

Теперь можно создать URL-адрес для доступа к WebHDFS следующим образом:

`https://<endpoint-security service external IP address>:30443/gateway/default/webhdfs/v1/`

Пример:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Список файлов

Файл списка в разделе **hdfs: / / / airlinedata**, используйте следующую команду curl:

```bash
curl -i -k -u root:root-password -X GET 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Локальный файл помещается в HDFS

Чтобы поместить новый файл **test.csv** из локального каталога в каталог airlinedata, используйте следующую команду curl ( **Content-Type** параметр является обязательным):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Создайте каталог

Чтобы создать каталог **тестирования** под `hdfs:///`, используйте следующую команду:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<endpoint-security IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о больших данных кластера SQL Server, см. в разделе [что такое большие данные кластера SQL Server?](big-data-cluster-overview.md).
