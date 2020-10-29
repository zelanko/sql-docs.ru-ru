---
title: Руководство по использованию шифрования неактивных данных (TDE) в Кластерах больших данных SQL Server
titleSuffix: SQL Server Big Data Clusters
description: В этой статье показано, как использовать функцию прозрачного шифрования неактивных данных SQL Server в BDC
author: DaniBunny
ms.author: dacoelho
ms.reviewer: mihaelab
ms.date: 10/19/2020
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 55456185a6503ee11465a1e65cb9cd91de3ba6e2
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92199585"
---
# <a name="sql-server-big-data-clusters-transparent-data-encryption-tde-at-rest-usage-guide"></a>Руководство по использованию шифрования неактивных данных (TDE) в Кластерах больших данных SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве показано, как использовать функции шифрования неактивных данных Кластеров больших данных SQL Server для шифрования баз данных.

Опыт работы в основном аналогичен SQL Server на Linux и при нем можно использовать [стандартную документацию по прозрачному шифрованию данных](../relational-databases/security/encryption/transparent-data-encryption.md), за исключением случаев, указанных выше. Чтобы отслеживать состояние шифрования в главном объекте, используйте стандартные шаблоны запросов динамического административного представления [`sys.dm_database_encryption_keys`](../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) и [`sys.certificates`](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md).

__Неподдерживаемые функции:__
* Шифрование пула данных
* Смена ключа шифрования для баз данных в автономной группе доступности в [развертывания с высоким уровнем доступности](deployment-high-availability.md).


## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

- [Кластер больших данных SQL Server CU8 +](release-notes-big-data-cluster.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **Azure Data Studio**
- Пользователь SQL Server с правами администратора.

## <a name="query-the-installed-certificates"></a>Создание запроса к установленным сертификатам

1. В Azure Data Studio установите подключение к главному экземпляру SQL Server в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к главному экземпляру SQL Server](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в окне **Серверы** , чтобы открыть панель мониторинга сервера для главного экземпляра SQL Server. Выберите **Создать запрос** .

   ![Запрос главного экземпляра SQL Server](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Выполните следующую команду Transact-SQL, чтобы изменить контекст **основной** базы данных в главном экземпляре.

   ```sql
   USE master
   GO
   ```

1. Создайте запрос установленных управляемых системой сертификатов. 

   ```sql
    SELECT TOP 1 name FROM sys.certificates WHERE name LIKE 'TDECertificate%' ORDER BY name DESC
   ```

    При необходимости используйте другие критерии запроса.

    Имя сертификата будет указано как: "TDECertificate {timestamp}". Если вы видите префикс TDECertificate и следующую за ним метку времени — это сертификат, предоставляемый функцией, управляемой системой.

## <a name="encrypt-a-database-using-the-system-provided-certificate"></a>Шифрование базы данных с помощью предоставленного системой сертификата

В следующих примерах мы используем как цель шифрования базу данных с именем __userdb__ и сертификат, предоставленный системой, с именем __TDECertificate2020_09_15_22_46_27__ для вывода, полученного при прохождении предыдущего раздела.

1. Используйте следующий шаблон, чтобы создать ключ шифрования базы данных с помощью предоставленного системного сертификата.

   ```sql
    USE userdb; 
    GO
    CREATE DATABASE ENCRYPTION KEY WITH ALGORITHM = AES_256 ENCRYPTION BY SERVER CERTIFICATE TDECertificate2020_09_15_22_46_27;
    GO
   ```

1. Зашифруйте базу данных __userdb__ с помощью следующей команды.

   ```sql
    ALTER DATABASE userdb SET ENCRYPTION ON;
    GO
   ```

## <a name="next-steps"></a>Дальнейшие действия

Узнайте больше о шифровании неактивных данных для HDFS:
> [!div class="nextstepaction"]
> [Зоны шифрования HDFS](encryption-at-rest-hdfs-encryption-zones.md)
