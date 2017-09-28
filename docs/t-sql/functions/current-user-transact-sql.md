---
title: "Функция CURRENT_USER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURRENT_USER
- CURRENT_USER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- current user names
- niladic functions
- CURRENT_USER
- users [SQL Server], names
ms.assetid: 29248949-325b-4063-9f55-5a445fb35c6e
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9edbc344723da335de150f5e829820eaef1d983e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="currentuser-transact-sql"></a>CURRENT_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает имя текущего пользователя. Эта функция эквивалента функции USER_NAME().
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CURRENT_USER  
```  

## <a name="return-types"></a>Возвращаемые типы
**sysname**
  
## <a name="remarks"></a>Замечания  
Функция CURRENT_USER возвращает имя текущего контекста безопасности. Если CURRENT_USER выполняется после вызова EXECUTE AS для переключения контекста, функция CURRENT_USER возвращает имя олицетворенного контекста. Если участник Windows обратился к базе данных в качестве участника группы, вместо имени группы возвращается имя участника Windows.
  
Чтобы возвратить имя входа текущего пользователя, см. [SUSER_NAME &#40; Transact-SQL &#41; ](../../t-sql/functions/suser-name-transact-sql.md) и [SYSTEM_USER &#40; Transact-SQL &#41; ](../../t-sql/functions/system-user-transact-sql.md).
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-currentuser-to-return-the-current-user-name"></a>A. Использование ключевого слова CURRENT_USER для возврата имени текущего пользователя  
В следующем примере возвращается имя текущего пользователя.
  
```sql
SELECT CURRENT_USER;  
GO  
```  
  
### <a name="b-using-currentuser-as-a-default-constraint"></a>Б. Использование ключевого слова CURRENT_USER в качестве ограничения DEFAULT  
В следующем примере создается таблица, использующая функцию `CURRENT_USER` в качестве ограничения `DEFAULT` для столбца `order_person` на строке продаж.
  
```sql
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'orders22')  
   DROP TABLE orders22;  
GO  
SET NOCOUNT ON;  
CREATE TABLE orders22  
(  
order_id int IDENTITY(1000, 1) NOT NULL,
cust_id  int NOT NULL,
order_date smalldatetime NOT NULL DEFAULT GETDATE(),
order_amt money NOT NULL,
order_person char(30) NOT NULL DEFAULT CURRENT_USER
);  
GO  
```  
  
Следующий код осуществляет вставку записи в таблицу. Пользователь, выполняющий эти инструкции, имеет имя `Wanida`.
  
```sql
INSERT orders22 (cust_id, order_amt)  
VALUES (5105, 577.95);  
GO  
SET NOCOUNT OFF;  
GO  
```  
  
Следующий запрос выбирает все данные из таблицы `orders22`.
  
```sql
SELECT * FROM orders22;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`order_id    cust_id     order_date           order_amt    order_person`
  
`----------- ----------- -------------------- ------------ ------------`
  
`1000        5105        2005-04-03 23:34:00  577.95       Wanida`
  
`(1 row(s) affected)`
  
### <a name="c-using-currentuser-from-an-impersonated-context"></a>В. Использование ключевого слова CURRENT_USER из олицетворенного контекста  
В следующем примере пользователь `Wanida` выполняет следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
```sql
SELECT CURRENT_USER;  
GO  
EXECUTE AS USER = 'Arnalfo';  
GO  
SELECT CURRENT_USER;  
GO  
REVERT;  
GO  
SELECT CURRENT_USER;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`Wanida`
  
`Arnalfo`
  
`Wanida`
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-currentuser-to-return-the-current-user-name"></a>D: использование ключевого слова CURRENT_USER для возврата имени текущего пользователя  
В следующем примере возвращается имя текущего пользователя.
  
```sql
SELECT CURRENT_USER;  
```  
  
## <a name="see-also"></a>См. также:
[Имя_пользователя &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)  
[Функция SYSTEM_USER &#40; Transact-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)  
[sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


