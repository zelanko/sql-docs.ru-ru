---
title: Подключение в режиме Active Directory
titleSuffix: SQL Server Big Data Cluster
description: Узнайте, как подключаться к кластерам больших данных SQL Server в домене Active Directory.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bd8da3642d0a650ea10c54b7ed8e46a54fba2971
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91898742"
---
# <a name="connect-big-data-clusters-2019-active-directory-mode"></a>Подключение [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]. Режим Active Directory

В этой статье описывается подключение к конечным точкам кластера больших данных SQL Server, развернутого в режиме Active Directory. Для выполнения задач в этой статье требуется, чтобы кластер больших данных SQL Server был развернут в режиме Active Directory. Если у вас нет кластера, см. раздел [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](active-directory-deploy.md).

## <a name="overview"></a>Обзор

Войдите в основной экземпляр SQL Server, используя проверку подлинности AD.

Чтобы проверить подключения AD к экземпляру SQL Server, подключитесь к основному экземпляру SQL с помощью `sqlcmd` При развертывании для подготовленных групп автоматически создаются данные для входа (`clusterUsers` и `clusterAdmins`).

Если вы используете Linux, сначала запустите `kinit` от имени пользователя AD, а затем запустите `sqlcmd`. Если вы используете Windows, просто войдите в систему от имени нужного пользователя с **подключенного к домену клиентского компьютера**.

## <a name="connect-to-master-instance-from-linuxmac"></a>Подключение к основному экземпляру из Linux или Mac

```bash
kinit <username>@<domain name>
sqlcmd -S <DNS name for master instance>,31433 -E
```

## <a name="connect-to-master-instance-from-windows"></a>Подключение к основному экземпляру из Windows

```cmd
sqlcmd -S <DNS name for master instance>,31433 -E
```

## <a name="log-in-to-sql-server-master-instance-using-azure-data-studio-or-ssms"></a>Вход в основной экземпляр SQL Server с использованием Azure Data Studio или SSMS

Из подключенного к домену клиента можно открыть SSMS или Azure Data Studio и подключиться к основному экземпляру. Процедура схожа с подключением к любому экземпляру SQL Server с использованием проверки подлинности AD.

С помощью SSMS:

![Диалоговое окно "Подключение к SQL Server" в SSMS](./media/deploy-active-directory/image23.png)

С помощью Azure Data Studio:

![Диалоговое окно "Подключение к SQL Server" в Azure Data Studio](./media/deploy-active-directory/image24.png)}

## <a name="log-in-to-controller-with-ad-authentication"></a>Вход в контроллер с проверкой подлинности AD

### <a name="connect-to-controller-with-ad-authentication-from-linuxmac"></a>Подключение к контроллеру с помощью проверки подлинности AD из Linux или Mac

Существует два варианта подключения к конечной точке контроллера, используя `azdata` и проверку подлинности AD. Можно использовать параметр *--endpoint/-e*.

```bash
kinit <username>@<domain name>
azdata login -e https://<controller DNS name>:30080 --auth ad
```

Кроме того, можно подключиться с использованием параметра *--namespace/-n*, который является именем кластера больших данных.

```bash
kinit <username>@<domain name>
azdata login -n <clusterName> --auth ad
```

### <a name="connect-to-controller-with-ad-authentication-from-windows"></a>Подключение к контроллеру с проверкой подлинности AD из Windows

```cmd
azdata login -e https://<controller DNS name>:30080 --auth ad
```

## <a name="use-ad-authentication-to-knox-gateway-webhdfs"></a>Использование проверки подлинности AD для шлюза Knox (webHDFS)

Отправлять команды HDFS также можно через конечную точку шлюза Knox с помощью curl. Для этого требуется проверка подлинности AD в Knox. Приведенная ниже команда curl отправляет вызов webHDFS REST через шлюз Knox для создания каталога `products`

```bash
curl -k -v --negotiate -u : https://<Gateway DNS name>:30443/gateway/default/webhdfs/v1/products?op=MKDIRS -X PUT
```

## <a name="next-steps"></a>Дальнейшие действия

[Устранение неполадок при интеграции кластера больших данных SQL Server с Active Directory](troubleshoot-active-directory.md)

[Концепция: развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в режиме Active Directory](active-directory-deployment-background.md)
