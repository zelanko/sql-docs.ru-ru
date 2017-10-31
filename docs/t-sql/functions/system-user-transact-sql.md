---
title: "Функция SYSTEM_USER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSTEM_USER_TSQL
- SYSTEM_USER
dev_langs:
- TSQL
helpviewer_keywords:
- current user names
- system-supplied user names [SQL Server]
- users [SQL Server], logins
- logins [SQL Server], identification name
- current system user names
- SYSTEM_USER function
- inserting system user name into table
- system usernames [SQL Server]
- users [SQL Server], names
ms.assetid: 565984cd-60c6-4df7-83ea-2349b838ccb2
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3f13d5db5d7787a60c455edc64644f4c23779fc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="systemuser-transact-sql"></a>SYSTEM_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Позволяет вставить в таблицу значение текущего имени входа, назначенного системой, если не задано значение по умолчанию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SYSTEM_USER  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nchar**  
  
## <a name="remarks"></a>Замечания  
 Функцию SYSTEM_USER можно использовать с ограничениями DEFAULT в инструкциях CREATE TABLE и ALTER TABLE. Она также может использоваться как стандартная функция.  
  
 Если имя пользователя и имя входа различаются, функция SYSTEM_USER возвращает имя входа.  
  
 Если текущий пользователь подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows, функция SYSTEM_USER возвращает идентификационное имя учетной записи Windows в виде: *домена*\\*user_login_name*. Однако, если текущий пользователь подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с проверкой подлинности SQL Server, функция SYSTEM_USER возвращает имя входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например `WillisJo`, для пользователя, подключившегося как `WillisJo`.  
  
 Функция SYSTEM_USER возвращает имя текущего выполняемого контекста. Если контекст был переключен с помощью инструкции EXECUTE AS, функция SYSTEM_USER возвращает имя олицетворяемого контекста.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-systemuser-to-return-the-current-system-user-name"></a>A. Использование функции SYSTEM_USER для получения текущего системного имени пользователя  
 В следующем примере объявляется переменная `char`, в которой сохраняется текущее значение `SYSTEM_USER`, а затем значение этой переменной выводится на печать.  
  
```  
DECLARE @sys_usr char(30);  
SET @sys_usr = SYSTEM_USER;  
SELECT 'The current system user is: '+ @sys_usr;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
----------------------------------------------------------
The current system user is: WillisJo

(1 row(s) affected)
 ```  
  
### <a name="b-using-systemuser-with-default-constraints"></a>Б. Использование функции SYSTEM_USER с ограничениями DEFAULT  
 В следующем примере создается таблица с функцией `SYSTEM_USER` в качестве ограничения `DEFAULT` для столбца `SRep_tracking_user`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE Sales.Sales_Tracking  
(  
    Territory_id int IDENTITY(2000, 1) NOT NULL,  
    Rep_id  int NOT NULL,  
    Last_sale datetime NOT NULL DEFAULT GETDATE(),  
    SRep_tracking_user varchar(30) NOT NULL DEFAULT SYSTEM_USER  
);  
GO  
INSERT Sales.Sales_Tracking (Rep_id)  
VALUES (151);  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (293, '19980515');  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (27882, '19980620');  
INSERT Sales.Sales_Tracking (Rep_id)  
VALUES (21392);  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (24283, '19981130');  
GO  
```  
  
 Следующий запрос позволяет выбрать все данные из таблицы `Sales_Tracking`:  
  
```  
SELECT * FROM Sales_Tracking ORDER BY Rep_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Territory_id Rep_id Last_sale            SRep_tracking_user
-----------  ------ -------------------- ------------------
2000         151    Mar 4 1998 10:36AM   ArvinDak
2001         293    May 15 1998 12:00AM  ArvinDak
2003         21392  Mar 4 1998 10:36AM   ArvinDak
2004         24283  Nov 3 1998 12:00AM   ArvinDak
2002         27882  Jun 20 1998 12:00AM  ArvinDak
  
(5 row(s) affected)
 ```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-systemuser-to-return-the-current-system-user-name"></a>C: использование функции SYSTEM_USER для получения текущего системного имени пользователя  
 В следующем примере возвращается текущее значение `SYSTEM_USER`.  
  
```  
SELECT SYSTEM_USER;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40; Transact-SQL &#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [Функция CURRENT_USER &#40; Transact-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [Функция SESSION_USER &#40; Transact-SQL &#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [&#40; пользователя Transact-SQL &#41;](../../t-sql/functions/user-transact-sql.md)  
  
  


