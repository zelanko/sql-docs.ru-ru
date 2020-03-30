---
title: '@@NESTLEVEL (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@NESTLEVEL'
- '@@NESTLEVEL_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@NESTLEVEL function'
- nesting stored procedures
- stored procedure nesting levels [SQL Server]
ms.assetid: 8c0b2134-8616-44f6-addc-6583c432fb62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d9b391d58d8a55b7486cda447d13246df16093b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68130146"
---
# <a name="x40x40nestlevel-transact-sql"></a>&#x40;&#x40;NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает уровень вложенности выполняющейся в данный момент хранимой процедуры (изначально равен 0).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@NESTLEVEL  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 Каждый раз, когда хранимая процедура вызывает другую хранимую процедуру или выполняет управляемый код путем обращения к подпрограмме, типу или статистическому выражению среды CLR, уровень вложенности возрастает. При достижении максимального уровня 32 транзакция прекращается.  
  
 Если функция @@NESTLEVEL выполняется внутри строки на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], возвращается значение 1 + текущий уровень вложенности. Если функция @@NESTLEVEL выполняется динамически с помощью процедуры sp_executesql, возвращается значение 2 + текущий уровень вложенности.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-nestlevel-in-a-procedure"></a>A. Использование @@NESTLEVEL в процедуре  
 В следующем примере создаются две процедуры: первая вызывает вторую, а вторая отображает параметр `@@NESTLEVEL` каждой из процедур.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'usp_OuterProc', N'P')IS NOT NULL  
    DROP PROCEDURE usp_OuterProc;  
GO  
IF OBJECT_ID (N'usp_InnerProc', N'P')IS NOT NULL  
    DROP PROCEDURE usp_InnerProc;  
GO  
CREATE PROCEDURE usp_InnerProc AS   
    SELECT @@NESTLEVEL AS 'Inner Level';  
GO  
CREATE PROCEDURE usp_OuterProc AS   
    SELECT @@NESTLEVEL AS 'Outer Level';  
    EXEC usp_InnerProc;  
GO  
EXECUTE usp_OuterProc;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Outer Level  
-----------  
1  
  
Inner Level  
-----------  
2
```  
  
### <a name="b-calling-nestlevel"></a>Б. Вызов @@NESTLEVEL  
 В приведенном ниже примере показана разница значений, возвращаемых инструкциями `SELECT`, `EXEC` и хранимой процедурой `sp_executesql`, когда каждая из них вызывает функцию `@@NESTLEVEL`.  
  
```  
CREATE PROC usp_NestLevelValues AS  
    SELECT @@NESTLEVEL AS 'Current Nest Level';  
EXEC ('SELECT @@NESTLEVEL AS OneGreater');   
EXEC sp_executesql N'SELECT @@NESTLEVEL as TwoGreater' ;  
GO  
EXEC usp_NestLevelValues;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Current Nest Level  
------------------  
1  
  
(1 row(s) affected)  
  
OneGreater  
-----------  
2  
  
(1 row(s) affected)  
  
TwoGreater  
-----------  
3  
  
(1 row(s) affected)
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Создание хранимой процедуры](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
