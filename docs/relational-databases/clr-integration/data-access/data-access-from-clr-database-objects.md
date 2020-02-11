---
title: Доступ к данным из объектов базы данных CLR | Документация Майкрософт
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
ms.openlocfilehash: 29110ecb83493ec95fbc594d0f743c3c4cb07a68
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68216400"
---
# <a name="data-access-from-clr-database-objects"></a>Доступ к данным из объектов среды CLR для работы с базами данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Подпрограммы среды CLR могут легко обращаться к данным, хранящимся в экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служб, в котором она выполняется, а также к данным, хранящимся в удаленных экземплярах. Какие именно это данные — определяет контекст пользователя, в котором выполняется код. Доступ к данным из объекта базы данных CLR с помощью .NET Framework поставщика данных для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который также называется **SqlClient**. Это тот же поставщик, который используется разработчиками для доступа к данным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из управляемого клиента и приложений среднего уровня. По этой причине вы можете использовать знания ADO.NET и **SqlClient** в клиентских и промежуточных приложениях.  
  
> [!NOTE]  
>  По умолчанию методы определяемых пользователем типов и определяемые пользователем функции не могут производить доступ к данным. Необходимо установить свойство **доступа** **склмесодаттрибуте** или **SqlFunctionAttribute** в **DataAccessKind. Read** , чтобы разрешить доступ к данным только для чтения из методов определяемого пользователем типа или определяемых пользователем функций. Операции изменения данных из методов определяемых пользователем типов и определяемых пользователем функций не разрешены. При попытке выполнить такую операцию будет вызвано исключение времени выполнения.  
  
 В этом разделе приведены лишь особые функциональные и поведенческие различия при доступе к данным из объекта базы данных CLR. Дополнительные сведения о функциях и возможностях ADO.NET см. в документации по ADO.NET, включенной в пакет разработчика .NET Framework SDK.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
 Содержит сведения о контекстном соединении с SQL Server.  
  
 [Олицетворение и учетные данные для соединений](../../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
 Содержит сведения об олицетворенных соединениях и учетных данных соединения.  
  
 [Внутрипроцессные расширения SQL Server для ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 Описывает внутрипроцессный объект **SqlPipe**, **SqlContext**, **SqlTriggerContext**и **SqlDataRecord** .  
  
 [Интеграция со средой CLR и транзакции](../../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
 Содержит описание интеграции с ADO.NET и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR новой платформы транзакций, представленной в пространстве имен System.Transactions.  
  
 [Сериализация XML из объектов базы данных CLR](https://msdn.microsoft.com/library/ac84339b-9384-4710-bebc-01607864a344)  
 Объясняет, как задействовать сценарии сериализации XML объектов базы данных CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
