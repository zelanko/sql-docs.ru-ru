---
title: "GO (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- GO
- GO_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- batches [SQL Server], ending
- ending batches [SQL Server]
- GO command
ms.assetid: b2ca6791-3a07-4209-ba8e-2248a92dd738
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b78d6ca719088ade9d54db73b8ee10ef8072a5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-utilities-statements---go"></a>Инструкции служебных программ SQL Server - GO
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет команды, которые не являются [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, но распознаются **sqlcmd** и **osql** служебных программ и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] редактора кода. Эти команды используются для повышения удобочитаемости и упрощения выполнения пакетов и скриптов.  
  
  GO обозначает конец пакета [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служебных программ.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GO [count]  
```  
  
## <a name="arguments"></a>Аргументы  
 *count*  
 Целое положительное число. Пакет, предшествующий команде GO, будет выполняться заданное количество раз.  
  
## <a name="remarks"></a>Замечания  
 Ключевое слово GO является не [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции; оно команду распознается **sqlcmd** и **osql** служебные программы и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] редактор кода.  
  
 Программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретируют команду GO как сигнал о том, что им следует отправить текущий пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Текущий пакет инструкций состоит из всех инструкций, введенных за время, прошедшее с момента обработки последней команды GO, или, если данная команда GO является первой, с момента начала нерегламентированного сеанса или скрипта.  
  
 Инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] не может располагаться на той же строке, что и команда GO. Тем не менее строка с командой GO может содержать комментарии.  
  
 При использовании команды GO нужно соблюдать требования, предъявляемые к пакетам. Например, при любом вызове хранимой процедуры после первой инструкции пакета нужно использовать ключевое слово EXECUTE. Область видимости локальных (пользовательских) переменных ограничена пакетом, и к ним нельзя обращаться после команды GO.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyMsg VARCHAR(50)  
SELECT @MyMsg = 'Hello, World.'  
GO -- @MyMsg is not valid after this GO ends the batch.  
  
-- Yields an error because @MyMsg not declared in this batch.  
PRINT @MyMsg  
GO  
  
SELECT @@VERSION;  
-- Yields an error: Must be EXEC sp_who if not first statement in   
-- batch.  
sp_who  
GO  
```  
  
 Приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут отправлять экземпляру [!INCLUDE[tsql](../../includes/tsql-md.md)] множественные инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы они были выполнены как пакет. Инструкции пакета компилируются в единый план выполнения. Программисты, выполняющие в программах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нерегламентированные инструкции или составляющие из инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипты для программ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используют команду GO как сигнал об окончании пакета.  
  
 Приложения, основанные на API-интерфейсах ODBC или OLE DB, при попытке выполнить команду GO получают уведомление о синтаксической ошибке. Программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] никогда не отправляют команду GO серверу.  
  
 Не используйте точку с запятой в качестве признака конца инструкции после команды GO.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения команды GO не требуются какие-либо разрешения. Она может быть выполнена любым пользователем.  
  
```  
-- Yields an error because ; is not permitted after GO  
SELECT @@VERSION;  
GO;  
```  
  
## <a name="examples"></a>Примеры  
 В следующем примере создаются два пакета. Первый содержит только `USE``AdventureWorks2012` инструкции, чтобы задать контекст базы данных. Остальные инструкции выполняют те или иные операции над локальной переменной и должны быть сгруппированы в один пакет. Поэтому следующая команда `GO` указывается только после последней инструкции, в которой используется переменная.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @NmbrPeople int  
SELECT @NmbrPeople = COUNT(*)  
FROM Person.Person;  
PRINT 'The number of people as of ' +  
      CAST(GETDATE() AS char(20)) + ' is ' +  
      CAST(@NmbrPeople AS char (10));  
GO  
```  
  
 В следующем примере инструкции в пакете выполняются дважды.  
  
```  
SELECT DB_NAME();  
SELECT USER_NAME();  
GO 2  
```  
  
  

