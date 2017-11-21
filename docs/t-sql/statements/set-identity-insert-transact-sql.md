---
title: "SET IDENTITY_INSERT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET IDENTITY_INSERT
- SET_IDENTITY_INSERT_TSQL
- IDENTITY_INSERT_TSQL
- IDENTITY_INSERT
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY_INSERT option
- SET IDENTITY_INSERT statement
- identity values [SQL Server], explicit values
- identity columns [SQL Server], explicit values
ms.assetid: a5dd49f2-45c7-44a8-b182-e0a5e5c373ee
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9725d774075f21fc86d5276c91ed281fa34eba7d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-identityinsert-transact-sql"></a>SET IDENTITY_INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Позволяет вставлять явные значения в столбец идентификаторов таблицы.  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET IDENTITY_INSERT [ database_name . [ schema_name ] . ] table { ON | OFF }  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, в которой находится указанная таблица.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица.  
  
 *table*  
 Имя таблицы со столбцом идентификаторов.  
  
## <a name="remarks"></a>Замечания  
 В каждый момент времени только для одной таблицы в сеансе свойство IDENTITY_INSERT может принимать значение ON. Если у какой-то таблицы это свойство уже имеет значение ON и инструкция SET IDENTITY_INSERT ON адресована другой таблице, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернет сообщение об ошибке, в котором будет сказано, что свойство SET IDENTITY_INSERT уже приняло значение ON, и приведено имя соответствующей таблицы.  
  
 Если вставляемое значение больше текущего значения идентификатора в данной таблице, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически будет использовать вставленное значение в качестве текущего.  
  
 Задание параметра SET IDENTITY_INSERT происходит во время выполнения или запуска инструкций, а не их синтаксического анализа.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен быть владельцем таблицы или иметь разрешение ALTER на таблицу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается таблица со столбцом идентификаторов, и показывается, как можно использовать параметр `SET IDENTITY_INSERT` для заполнения промежутков между значениями идентификаторов, вызванных выполнением инструкции `DELETE`.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create tool table.  
CREATE TABLE dbo.Tool(  
   ID INT IDENTITY NOT NULL PRIMARY KEY,   
   Name VARCHAR(40) NOT NULL  
);  
GO  
-- Inserting values into products table.  
INSERT INTO dbo.Tool(Name)   
VALUES ('Screwdriver')  
        , ('Hammer')  
        , ('Saw')  
        , ('Shovel');  
GO  
  
-- Create a gap in the identity values.  
DELETE dbo.Tool  
WHERE Name = 'Saw';  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
  
-- Try to insert an explicit ID value of 3;  
-- should return a warning.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
-- SET IDENTITY_INSERT to ON.  
SET IDENTITY_INSERT dbo.Tool ON;  
GO  
  
-- Try to insert an explicit ID value of 3.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
-- Drop products table.  
DROP TABLE dbo.Tool;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Свойство IDENTITY (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

