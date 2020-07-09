---
title: '@@PROCID (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@PROCID'
- '@@PROCID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server], identification numbers
- UDTs [SQL Server], object identifiers
- '@@PROCID function'
- user-defined functions [SQL Server], object identifiers
- triggers [SQL Server], object identifiers
- identification numbers [SQL Server], modules
- IDs [SQL Server], modules
- module object identifiers [SQL Server]
ms.assetid: 0d4882c7-edb8-49b1-a470-2c7497b8998f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 092b4dee65e98678e97fa7eb3501793d8e466ac6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737925"
---
# <a name="x40x40procid-transact-sql"></a>&#x40;&#x40;PROCID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает идентификатор объекта (ID) текущего модуля [!INCLUDE[tsql](../../includes/tsql-md.md)]. Модуль [!INCLUDE[tsql](../../includes/tsql-md.md)] может быть хранимой процедурой, определяемой пользователем функцией или триггером. Функция @@PROCID не может быть вызвана из модулей среды CLR или внутрипроцессного поставщика доступа к данным.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@PROCID  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция `@@PROCID` используется в качестве входного параметра функции `OBJECT_NAME` для возврата имени хранимой процедуры в тексте сообщения `RAISERROR`.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'usp_FindName', 'P' ) IS NOT NULL   
DROP PROCEDURE usp_FindName;  
GO  
CREATE PROCEDURE usp_FindName  
    @lastname varchar(40) = '%',   
    @firstname varchar(20) = '%'  
AS  
DECLARE @Count int;  
DECLARE @ProcName nvarchar(128);  
SELECT LastName, FirstName  
FROM Person.Person   
WHERE FirstName LIKE @firstname AND LastName LIKE @lastname;  
SET @Count = @@ROWCOUNT;  
SET @ProcName = OBJECT_NAME(@@PROCID);  
RAISERROR ('Stored procedure %s returned %d rows.', 16,10, @ProcName, @Count);  
GO  
EXECUTE dbo.usp_FindName 'P%', 'A%';  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md)   
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
