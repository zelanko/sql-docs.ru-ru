---
title: Доступ к данным из объектов базы данных CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
caps.latest.revision: 41
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34a3fba5d3026601994d8c258ea35b87cbf5d4bf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-access-from-clr-database-objects"></a>Доступ к данным из объектов среды CLR для работы с базами данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Общие подпрограммы среды выполнения (CLR) языка может легко получить доступ к данным, хранящимся в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в котором она выполняется, а также данных, хранящихся на удаленных экземплярах. Какие именно это данные — определяет контекст пользователя, в котором выполняется код. Доступ к данным из объекта базы данных среды CLR, используя поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые также называются **SqlClient**. Это тот же поставщик, который используется разработчиками для доступа к данным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из управляемого клиента и приложений среднего уровня. По этой причине можно использовать знание ADO.NET и **SqlClient** в приложениях клиента и среднего уровня.  
  
> [!NOTE]  
>  По умолчанию методы определяемых пользователем типов и определяемые пользователем функции не могут производить доступ к данным. Необходимо задать **DataAccess** свойство **SqlMethodAttribute** или **SqlFunctionAttribute** для **DataAccessKind.Read** для включения доступ к данным только для чтения из методов определяемых пользователем типов (UDT) или определяемые пользователем функции. Операции изменения данных из методов определяемых пользователем типов и определяемых пользователем функций не разрешены. При попытке выполнить такую операцию будет вызвано исключение времени выполнения.  
  
 В этом разделе приведены лишь особые функциональные и поведенческие различия при доступе к данным из объекта базы данных CLR. Дополнительные сведения о функциях и возможностях ADO.NET см. в документации по ADO.NET, включенной в пакет разработчика .NET Framework SDK.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 Содержит сведения о контекстном соединении с SQL Server.  
  
 [Олицетворение и учетные данные для соединений](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 Содержит сведения об олицетворенных соединениях и учетных данных соединения.  
  
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Описание внутрипроцессных **SqlPipe**, **SqlContext**, **SqlTriggerContext**, и **SqlDataRecord** объектов.  
  
 [Интеграция со средой CLR и транзакции](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 Содержит описание интеграции с ADO.NET и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR новой платформы транзакций, представленной в пространстве имен System.Transactions.  
  
 [Сериализация XML из объектов базы данных CLR](http://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 Объясняет, как задействовать сценарии сериализации XML объектов базы данных CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
