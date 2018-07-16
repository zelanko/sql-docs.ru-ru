---
title: Доступ к данным из объектов базы данных CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
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
ms.openlocfilehash: 1c49134c931bc9f27e7c4856ce23ccde70364000
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351146"
---
# <a name="data-access-from-clr-database-objects"></a>Доступ к данным из объектов среды CLR для работы с базами данных
  Общие процедуры среды выполнения (CLR) языка может легко получить доступ к данных, хранящихся в экземпляре [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] в котором она выполняется, а также данные, хранящиеся на удаленных экземплярах. Какие именно это данные — определяет контекст пользователя, в котором выполняется код. Доступ к данным из объекта базы данных среды CLR, используя поставщик данных .NET Framework для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] данных из управляемого клиента и приложений среднего уровня. Это позволяет эффективно использовать опыт работы с ADO.NET и `SqlClient` как в клиентских приложениях, так и в приложениях среднего уровня.  
  
> [!NOTE]  
>  По умолчанию методы определяемых пользователем типов и определяемые пользователем функции не могут производить доступ к данным. Чтобы разрешить такой доступ, необходимо присвоить свойству `DataAccess` объекта `SqlMethodAttribute` или `SqlFunctionAttribute` значение `DataAccessKind.Read`. Операции изменения данных из методов определяемых пользователем типов и определяемых пользователем функций не разрешены. При попытке выполнить такую операцию будет вызвано исключение времени выполнения.  
  
 В этом разделе приведены лишь особые функциональные и поведенческие различия при доступе к данным из объекта базы данных CLR. Дополнительные сведения о функциях и возможностях ADO.NET см. в документации по ADO.NET, включенной в пакет разработчика .NET Framework SDK.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Контекстное соединение](context-connection.md)  
 Содержит сведения о контекстном соединении с SQL Server.  
  
 [Олицетворение и учетные данные для соединений](impersonation-and-credentials-for-connections.md)  
 Содержит сведения об олицетворенных соединениях и учетных данных соединения.  
  
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Содержит описание внутрипроцессных объектов `SqlPipe`, `SqlContext`, `SqlTriggerContext` и `SqlDataRecord`.  
  
 [Интеграция со средой CLR и транзакции](../../native-client-ole-db-transactions/transactions.md)  
 Содержит описание интеграции с ADO.NET и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR новой платформы транзакций, представленной в пространстве имен System.Transactions.  
  
 [Сериализация XML из объектов базы данных CLR](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 Объясняет, как задействовать сценарии сериализации XML объектов базы данных CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
