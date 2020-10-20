---
title: Загрузка данных в HDFS с помощью curl | Документация Майкрософт
titleSuffix: SQL Server big data clusters
description: Использование curl для загрузки данных в HDFS в кластерах больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ae893bb1e291b244b5101ccfb2ed66bcf765f049
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91866851"
---
# <a name="use-curl-to-load-data-into-hdfs-on-big-data-clusters-2019"></a>Загрузка данных в HDFS с помощью curl в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается использование **curl** для загрузки данных в HDFS в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].

## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

- [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md)

## <a name="obtain-the-service-external-ip"></a>Получение внешнего IP-адреса службы

WebHDFS запускается после завершения развертывания. Доступ к этой службе осуществляется через Knox. Конечная точка Knox предоставляется через службу Kubernetes **gateway-svc-external**.  Для создания необходимого URL-адреса WebHDFS для отправки или скачивания файлов потребуется внешний IP-адрес службы **gateway-svc-external** и имя кластера больших данных. Внешний IP-адрес службы **gateway-svc-external** можно получить, выполнив следующую команду:

```terminal
kubectl get service gateway-svc-external -n <big data cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<big data cluster name>` — это имя кластера, указанное в файле конфигурации развертывания. Имя по умолчанию имеет значение `mssql-cluster`.

## <a name="construct-the-url-to-access-webhdfs"></a>Создание URL-адреса для доступа к WebHDFS

Теперь можно создать URL-адрес для доступа к WebHDFS следующим образом:

`https://<gateway-svc-external service external IP address>:30443/gateway/default/webhdfs/v1/`

Пример:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="authentication-with-active-directory"></a>Проверка подлинности через Active Directory

Для развертываний с Active Directory используйте параметр проверки подлинности с `curl` с проверкой подлинности согласованием. 

Чтобы использовать `curl` с проверкой подлинности Active Directory, выполните следующую команду:

```
kinit <username>
```

Команда создает токен Kerberos для `curl`. Команды, показанные в следующих разделах, указывают параметр `--anyauth` для `curl`. Для URL-адресов, требующих проверки подлинности согласованием, `curl` автоматически обнаруживает и использует сгенерированный токен Kerberos вместо имени пользователя и пароля.

## <a name="list-a-file"></a>Указание файла

Чтобы указать файл в **hdfs:///product_review_data**, выполните следующую команду:

```terminal
curl -i -k --anyauth -u root:<AZDATA_PASSWORD> -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

Для конечных точек, не использующих корневую папку, выполните следующую команду cURL:

```terminal
curl -i -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X GET 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Размещение локального файла в HDFS

Чтобы разместить новый файл **test.csv** из локального каталога в каталоге product_review_data, выполните следующую команду curl (параметр **Content-Type** является обязательным):

```terminal
curl -i -L -k --anyauth -u root:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

Для конечных точек, не использующих корневую папку, выполните следующую команду cURL:

```terminal
curl -i -L -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/product_review_data/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Создание каталога

Чтобы создать каталог **test** в `hdfs:///`, выполните следующую команду:

```terminal
curl -i -L -k --anyauth -u root:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

[!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]
Для конечных точек, не использующих корневую папку, выполните следующую команду cURL:

```terminal
curl -i -L -k --anyauth -u <AZDATA_USERNAME>:<AZDATA_PASSWORD> -X PUT 'https://<gateway-svc-external IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных SQL Server см. в [этой статье](big-data-cluster-overview.md).
