---
title: Загрузка данных в HDFS с помощью curl | Документация Майкрософт
titleSuffix: SQL Server big data clusters
description: Используйте фигурные скобки для загрузки данных [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]в HDFS в.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 729c3af97f98bafced482f7ead8ce85f93b55af3
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652210"
---
# <a name="use-curl-to-load-data-into-hdfs-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Используйте фигурные скобки для загрузки данных в HDFS[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье объясняется, как использовать фигуру для загрузки данных [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] в HDFS (Предварительная версия).

## <a name="obtain-the-service-external-ip"></a>Получение внешнего IP-адреса службы

WebHDFS запускается после завершения развертывания. Доступ к этой службе осуществляется через Knox. Конечная точка Knox предоставляется через службу Kubernetes **gateway-svc-external**.  Для создания необходимого URL-адреса WebHDFS для отправки или скачивания файлов потребуется внешний IP-адрес службы **gateway-svc-external** и имя кластера больших данных. Внешний IP-адрес службы **gateway-svc-external** можно получить, выполнив следующую команду:

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` — это имя кластера, указанное в файле конфигурации развертывания. Имя по умолчанию — `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Создание URL-адреса для доступа к WebHDFS

Теперь можно создать URL-адрес для доступа к WebHDFS следующим образом:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Пример:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Указание файла

Чтобы указать файл в **hdfs:///airlinedata**, выполните следующую команду:

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Размещение локального файла в HDFS

Чтобы разместить новый файл **test.csv** из локального каталога в каталоге airlinedata, выполните следующую команду curl (параметр **Content-Type** является обязательным):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Создание каталога

Чтобы создать каталог **test** в `hdfs:///`, выполните следующую команду:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server см. в [этой статье](big-data-cluster-overview.md).
