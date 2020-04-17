---
title: Доступ к данным из объектов базы данных CLR (ru) Документы Майкрософт
description: Процедуры CLR могут получить доступ к данным из объекта базы данных CLR с помощью поставщика рамочных данных .NET для сервера S'L, также называемого SqlClient.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5fdd552b0954f0eda838743530ab94e73aa27067
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485268"
---
# <a name="data-access-from-clr-database-objects"></a>Доступ к данным из объектов среды CLR для работы с базами данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Режим выполнения общего языка (CLR) может легко получить [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] доступ к данным, хранящимся в случае, в котором он работает, а также к данным, хранящимся в удаленных экземплярах. Какие именно это данные — определяет контекст пользователя, в котором выполняется код. Доступ к данным внутри объекта базы данных CLR [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]с помощью поставщика рамочных данных .NET для , также **называемого SqlClient.** Это тот же поставщик, который используется разработчиками для доступа к данным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из управляемого клиента и приложений среднего уровня. Из-за этого вы можете использовать свои знания о ADO.NET и **SqlClient** в клиентских и средних приложений.  
  
> [!NOTE]  
>  По умолчанию методы определяемых пользователем типов и определяемые пользователем функции не могут производить доступ к данным. Необходимо установить свойство **DataAccess** **SqlMethodAttribute** или **SqlFunctionAttribute** на **DataAccessKind.Read,** чтобы обеспечить доступ к данным только для чтения из методов, определяемых пользователем (UDT) или функций, определяемых пользователем. Операции изменения данных из методов определяемых пользователем типов и определяемых пользователем функций не разрешены. При попытке выполнить такую операцию будет вызвано исключение времени выполнения.  
  
 В этом разделе приведены лишь особые функциональные и поведенческие различия при доступе к данным из объекта базы данных CLR. Дополнительные сведения о функциях и возможностях ADO.NET см. в документации по ADO.NET, включенной в пакет разработчика .NET Framework SDK.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 Содержит сведения о контекстном соединении с SQL Server.  
  
 [Олицетворение и учетные данные для соединений](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 Содержит сведения об олицетворенных соединениях и учетных данных соединения.  
  
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Обсуждается в процессе конкретных **объектов SqlPipe**, **SqlContext,** **SqlTriggerContext**и **SqlDataRecord.**  
  
 [Интеграция со средой CLR и транзакции](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 Содержит описание интеграции с ADO.NET и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR новой платформы транзакций, представленной в пространстве имен System.Transactions.  
  
 [Сериализация XML из объектов базы данных CLR](https://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 Объясняет, как задействовать сценарии сериализации XML объектов базы данных CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
