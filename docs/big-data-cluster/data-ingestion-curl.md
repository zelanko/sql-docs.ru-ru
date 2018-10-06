---
title: Используйте curl для загрузки данных в HDFS в SQL Server 2019 CTP-версии 2.0 | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 05ce2d4d848b7c244d672f6ab43cbcf09224e63f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796886"
---
# <a name="use-curl-to-load-data-into-hdfs-on-sql-server-2019-ctp-20"></a>Используйте curl для загрузки данных в HDFS в SQL Server 2019 CTP 2.0

В этой статье описываются способы использования **curl** для загрузки данных в HDFS в SQL Server 2019 CTP 2.0.

## <a name="obtain-the-service-external-ip"></a>Получить внешний IP-адрес службы

WebHDFS запускается после завершения развертывания, и доступ к нему осуществляется через Knox. Конечная точка Knox предоставляется через службу Kubernetes вызывается (для настоящего) **службы безопасности балансировки нагрузки**.  Для создания URL-адрес WebHDFS, необходимо использовать CURL для отправки или скачивания файлов, необходимо будет **службы безопасности балансировки нагрузки** службы внешний IP-адрес и имя кластера. Внешний IP-адрес службы безопасности балансировки нагрузки службы можно получить, выполнив следующую команду:

```bash
kubectl get service service-security-lb -n <cluster name> -o json | jq -r .status.loadBalancer.ingress[0].ip
```

> [!NOTE]
> `<cluster name>` Вот имя кластера, который использовался при запуске mssqlctl создание кластера `<cluster name>`.

## <a name="construct-the-url-to-access-webhdfs"></a>Создать URL-адрес для доступа к WebHDFS

Теперь можно создать URL-адрес для доступа к WebHDFS следующим образом:

`https://<service-security-lb service external IP address>:30433/gateway/default/webhdfs/v1/`

Пример:

`https://13.66.190.205:30443/gateway/default/webhdfs/v1/`

## <a name="list-a-file"></a>Список файлов

Файл списка в разделе **hdfs: / / / airlinedata** используйте следующую команду curl:

```bash
curl -i -k -u root:root-password -X GET 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/?op=liststatus'
```

## <a name="put-a-local-file-into-hdfs"></a>Локальный файл помещается в HDFS

Чтобы поместить новый файл **test.csv** из локального каталога в каталог airlinedata (**Content-Type** параметр является обязательным) используйте следующую команду curl:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/airlinedata/test.csv?op=create' -H 'Content-Type: application/octet-stream' -T 'test.csv'
```

## <a name="create-a-directory"></a>Создайте каталог

Чтобы создать каталог **тестирования** под `hdfs:///` используйте следующую команду:

```bash
curl -i -L -k -u root:root-password -X PUT 'https://<service-security-lb IP external address>:30443/gateway/default/webhdfs/v1/test?op=MKDIRS'
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о больших данных кластера SQL Server, см. в разделе [что такое большие данные кластера SQL Server?](big-data-cluster-overview.md).