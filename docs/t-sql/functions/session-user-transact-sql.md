---
title: "Функция SESSION_USER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SESSION_USER_TSQL
- SESSION_USER
dev_langs: TSQL
helpviewer_keywords:
- usernames [SQL Server]
- current user names
- sessions [SQL Server], user names
- displaying user names
- viewing user names
- SESSION_USER function
ms.assetid: 3dbe8532-31b6-4862-8b2a-e58b00b964de
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 96d5050eedfa87599b2b06a1e22b88bda45860e0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sessionuser-transact-sql"></a>SESSION_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Функция SESSION_USER возвращает имя пользователя текущего контекста в текущей базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SESSION_USER  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Замечания  
 Функция SESSION_USER с ограничением DEFAULT используется в инструкциях CREATE TABLE или ALTER TABLE, либо как любая стандартная функция. Функцию SESSION_USER можно вставить в таблицу, если не задано значения по умолчанию. Эта функция не имеет аргументов. Функция SESSION_USER может использоваться в запросах.  
  
 Если функция SESSION_USER вызывается после переключения контекста, SESSION_USER возвращает имя пользователя олицетворенного контекста.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-sessionuser-to-return-the-user-name-of-the-current-session"></a>A. Использование функции SESSION_USER для получения имени пользователя текущего сеанса  
 В следующем примере объявляется переменная типа `nchar`, ей присваивается текущее значение `SESSION_USER`, а затем эта переменная выводится на печать вместе с текстовым описанием.  
  
```  
DECLARE @session_usr nchar(30);  
SET @session_usr = SESSION_USER;  
SELECT 'This session''s current user is: '+ @session_usr;  
GO  
```  
  
 Ниже представлен результирующий набор, если пользователем сеанса является `Surya`:  
  
 ```
--------------------------------------------------------------
This session's current user is: Surya

(1 row(s) affected)
```  
  
### <a name="b-using-sessionuser-with-default-constraints"></a>Б. Использование функции SESSION_USER с ограничениями DEFAULT  
 В следующем примере создается таблица, которая использует `SESSION_USER` как ограничение `DEFAULT` для имени лица, регистрирующего прием отгрузки.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE deliveries3  
(  
 order_id int IDENTITY(5000, 1) NOT NULL,  
 cust_id  int NOT NULL,  
 order_date smalldatetime NOT NULL DEFAULT GETDATE(),  
 delivery_date smalldatetime NOT NULL DEFAULT   
    DATEADD(dd, 10, GETDATE()),  
 received_shipment nchar(30) NOT NULL DEFAULT SESSION_USER  
);  
GO  
```  
  
 Записи, добавленные к таблице, будут помечены именем текущего пользователя. В этом примере `Wanida`, `Sylvester` и `Alejandro` проверяют прием отгрузок. Это можно эмулировать, переключив контекст пользователя с помощью инструкции `EXECUTE AS`.  
  
```  
EXECUTE AS USER = 'Wanida'  
INSERT deliveries3 (cust_id)  
VALUES (7510);  
INSERT deliveries3 (cust_id)  
VALUES (7231);  
REVERT;  
EXECUTE AS USER = 'Sylvester'  
INSERT deliveries3 (cust_id)  
VALUES (7028);  
REVERT;  
EXECUTE AS USER = 'Alejandro'  
INSERT deliveries3 (cust_id)  
VALUES (7392);  
INSERT deliveries3 (cust_id)  
VALUES (7452);  
REVERT;  
GO  
```  
  
 Следующий запрос выбирает все данные из таблицы `deliveries3`.  
  
```  
SELECT order_id AS 'Order #', cust_id AS 'Customer #',   
   delivery_date AS 'When Delivered', received_shipment   
   AS 'Received By'  
FROM deliveries3  
ORDER BY order_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Order #   Customer #  When Delivered       Received By
--------  ----------  -------------------  -----------
5000      7510        2005-03-16 12:02:14  Wanida
5001      7231        2005-03-16 12:02:14  Wanida
5002      7028        2005-03-16 12:02:14  Sylvester
5003      7392        2005-03-16 12:02:14  Alejandro
5004      7452        2005-03-16 12:02:14  Alejandro

(5 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-sessionuser-to-return-the-user-name-of-the-current-session"></a>C: использование функции SESSION_USER для получения имени пользователя текущего сеанса  
 В следующем примере возвращается пользователем сеанса для текущего сеанса.  
  
```  
SELECT SESSION_USER;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40; Transact-SQL &#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [Функция CURRENT_USER &#40; Transact-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [Функция SYSTEM_USER &#40; Transact-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [&#40; пользователя Transact-SQL &#41;](../../t-sql/functions/user-transact-sql.md)   
 [Имя_пользователя &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)  
  
  

