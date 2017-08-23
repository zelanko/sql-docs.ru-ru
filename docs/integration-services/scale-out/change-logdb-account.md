---
title: "Изменить учетную запись для ведения журналов служб SSIS масштабное развертывание | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ec785459e5f9585776d83cde3f460c1e79367e46
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="change-the-account-for-scale-out-logging"></a>Изменить учетную запись для ведения журнала масштабное развертывание
При выполнении пакетов в масштабное развертывание, сообщения о событиях записываются в базу данных SSISDB автоматически созданные пользователем **MS_SSISLogDBWorkerAgentLogin ##**. Учетная запись этого пользователя используется проверка подлинности SQL Server. Изменение учетной записи, указанные ниже действия следующим образом:

## <a name="1-create-a-user-of-ssisdb"></a>1. Создание пользователя SSISDB
Инструкции создания пользователя базы данных см. в разделе [создается пользователь базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2. Добавьте пользователя к роли ssis_cluster_worker базы данных

Инструкции соединения роли базы данных см. в разделе [присоединение к роли](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-logging-information-in-ssisdb"></a>3. Обновить данные протоколирования в SSISDB
Вызовите хранимую процедуру [catalog]. [update_logdb_info] с Sql Server имя и строку соединения в качестве параметров.

#### <a name="example"></a>Пример
```tsql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4. Перезапустите службу шкалы Out работника

> [!NOTE]
> При использовании учетной записи пользователя Windows для ведения журнала, его необходимо одной учетной записи службы шкалы Out работника. В противном случае произойдет ошибка входа в SQL Server.
