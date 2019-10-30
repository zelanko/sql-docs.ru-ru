---
title: Загрузка данных в HDFS с помощью curl | Документация Майкрософт
titleSuffix: SQL Server big data clusters
description: Используйте фигурные скобки для загрузки данных в HDFS на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c65ce7fb6752240f0dd23a6dab195539146e7933
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049879"
---
# <a name="use-curl-to-load-data-into-hdfs-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Используйте фигурные скобки для загрузки данных в HDFS на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье объясняется, как использовать **фигуру** для загрузки данных в HDFS на [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Предварительная версия).

## <a id="prereqs"></a> предварительные требования

- [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>Получение внешнего IP-адреса службы

WebHDFS запускается после завершения развертывания. Доступ к этой службе осуществляется через Knox. Конечная точка Knox предоставляется через службу Kubernetes **gateway-svc-external**.  Для создания необходимого URL-адреса WebHDFS для отправки или скачивания файлов потребуется внешний IP-адрес службы **gateway-svc-external** и имя кластера больших данных. Внешний IP-адрес службы **gateway-svc-external** можно получить, выполнив следующую команду:

```bash
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` — это имя кластера, указанное в файле конфигурации развертывания. Имя по умолчанию имеет значение `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Создание URL-адреса для доступа к WebHDFS

Теперь можно создать URL-адрес для доступа к WebHDFS следующим образом:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Пример:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Указание файла

Чтобы получить список файлов в **HDFS:///product_review_data**, используйте следующую команду:

```bash
curl -i -k -u root:root-password -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Размещение локального файла в HDFS

Чтобы добавить новый файл **Test. csv** из локального каталога в каталог product_review_data, используйте следующую команду (параметр **Content-Type** является обязательным):

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Создание каталога

Чтобы создать каталог **test** в `hdfs:///`, выполните следующую команду:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server см. в [этой статье](big-data-cluster-overview.md).
