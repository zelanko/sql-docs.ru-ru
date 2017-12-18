---
title: "Изменение учетной записи для ведения журнала служб SSIS Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcedbe0d2c2ef2c2089af1e2a8b31fbeb75ce2fc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="change-the-account-for-scale-out-logging"></a>Изменение учетной записи для ведения журнала служб SSIS Scale Out
При выполнении пакетов в Scale Out сообщения событий регистрируются в журнале SSISDB с помощью создаваемого автоматически пользователя **##MS_SSISLogDBWorkerAgentLogin##**. Для входа этого пользователя в систему применяется проверка подлинности SQL Server. Чтобы изменить учетную запись, выполните следующие действия:

## <a name="1-create-a-user-of-ssisdb"></a>1. Создание пользователя SSISDB
Инструкции по созданию пользователя базы данных см. в разделе [Создание пользователя базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2. Добавление пользователя в роль базы данных ssis_cluster_worker

Инструкции по присоединению к роли базы данных см. в разделе [Присоединение к роли](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-logging-information-in-ssisdb"></a>3. Обновление сведений о ведении журнала SSISDB
Вызовите хранимую процедуру [catalog].[update_logdb_info], передав в качестве параметров имя SQL Server и строку подключения.

#### <a name="example"></a>Пример
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4. Перезапуск службы рабочей роли Scale Out

> [!NOTE]
> Если для ведения журналов применяется учетная запись пользователя Windows, под этой же учетной записью должна выполняться служба рабочей роли Scale Out. В противном случае произойдет ошибка входа в SQL Server.
