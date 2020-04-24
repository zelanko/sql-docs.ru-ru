---
title: PERMISSIONS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PERMISSIONS_TSQL
- PERMISSIONS
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], verifying
- current permission status
- users [SQL Server], permissions status
- checking permission status
- security [SQL Server], permissions
- verifying permission status
- testing permissions
- PERMISSIONS function
ms.assetid: 81625a56-b160-4424-91c5-1ce8b259a8e6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 764c2db99c78cb776ed500ff1b3b04170516efe2
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632621"
---
# <a name="permissions-transact-sql"></a>PERMISSIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает битовую карту, указывающую разрешения на инструкции, объекты и столбцы для текущего пользователя.  
  
 **Внимание!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте функции [fn_my_permissions](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md) и [Has_Perms_By_Name](../../t-sql/functions/has-perms-by-name-transact-sql.md). Постоянное использование функции PERMISSIONS может привести к понижению производительности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
PERMISSIONS ( [ objectid [ , 'column' ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *objectid*  
 Идентификатор защищаемого объекта. Если аргумент *objectid* не указан, то значение битовой карты содержит разрешения на выполнение инструкций для текущего пользователя; в противном случае битовая карта содержит разрешения в отношении защищаемого объекта для текущего пользователя. Указанный защищаемый объект должен находиться в текущей базе данных. Для определения значения аргумента [objectid](../../t-sql/functions/object-id-transact-sql.md) следует использовать функцию *OBJECT_ID*.  
  
 **'** *column* **'**  
 Необязательное имя столбца, для которого возвращаются данные о разрешениях. Имя столбца должно быть допустимым в таблице, указанной в аргументе *objectid*.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Remarks  
 С помощью функции PERMISSIONS можно определить, имеет ли текущий пользователь разрешения, необходимые для выполнения инструкции или предоставления разрешения другому пользователю с помощью инструкции GRANT.  
  
 Возвращаемые данные о разрешениях представляют собой 32-разрядную битовую карту.  
  
 Младшие 16 разрядов отражают разрешения, предоставленные пользователю, и разрешения, применяемые к группам Windows и предопределенным ролям сервера, членство в которых имеет текущий пользователь. Например, значение 66 (шестнадцатеричное значение 0x42), возвращаемое, если не задан аргумент *objectid*, указывает, что пользователь имеет разрешение выполнять инструкции CREATE TABLE (десятичное значение 2) и BACKUP DATABASE (десятичное значение 64).  
  
 Старшие 16 разрядов отражают разрешения, которые пользователь может предоставить другим пользователям с помощью инструкции GRANT. Старшие 16 разрядов интерпретируются точно так же, как и младшие 16 разрядов, описанные в следующих таблицах, но они сдвинуты влево на 16 разрядов (умножены на 65536). Например, 0x8 (десятичное значение 8) — бит, который означает разрешение INSERT, если указан аргумент *objectid*. А 0x80000 (десятичное значение 524288) указывает на возможность предоставления разрешения INSERT с помощью инструкции GRANT, так как 524288 = 8 x 65536.  
  
 Благодаря членству в ролях, пользователь, не имеющий разрешения выполнить инструкцию, может предоставить такое разрешение другому пользователю.  
  
 В таблице ниже приведены разряды, которым соответствуют разрешения на выполнение инструкций (аргумент *objectid* не указан).  
  
|Разряд (дес.)|Разряд (шест.)|Разрешение на инструкцию|  
|-----------------|-----------------|--------------------------|  
|1|0x1|CREATE DATABASE (только в базе данных master)|  
|2|0x2|CREATE TABLE|  
|4|0x4|CREATE PROCEDURE|  
|8|0x8|CREATE VIEW|  
|16|0x10|CREATE RULE|  
|32|0x20|CREATE DEFAULT|  
|64|0x40|BACKUP DATABASE|  
|128|0x80|BACKUP LOG|  
|256|0x100|Reserved|  
  
 В таблице ниже приведены разряды, которым соответствуют разрешения на объекты, возвращаемые, только если указан аргумент *objectid*.  
  
|Разряд (дес.)|Разряд (шест.)|Разрешение на инструкцию|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT ALL|  
|2|0x2|UPDATE ALL|  
|4|0x4|REFERENCES ALL|  
|8|0x8|INSERT|  
|16|0x10|DELETE|  
|32|0x20|EXECUTE (только процедуры)|  
|4096|0x1000|SELECT ANY (по крайней мере один столбец)|  
|8192|0x2000|UPDATE ANY|  
|16384|0x4000|REFERENCES ANY|  
  
 В таблице ниже приведены разряды, которым соответствуют разрешения на объекты уровня столбцов, возвращаемые, только если указаны аргумент *objectid* и столбец.  
  
|Разряд (дес.)|Разряд (шест.)|Разрешение на инструкцию|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT|  
|2|0x2|UPDATE|  
|4|0x4|REFERENCES|  
  
 Значение NULL возвращается, если указанный параметр представляет собой NULL или недопустим (например, объект, заданный аргументом *objectid*, или столбец не существуют). Битовые значения для неприменимых разрешений (например, разрешение EXECUTE для таблицы, разряды 0x20) не определены.  
  
 Для определения каждого установленного бита в битовой карте, возвращаемой функцией PERMISSIONS, используйте оператор побитового AND (&).  
  
 Системная хранимая процедура sp_helprotect также может быть использована для получения списка разрешений для пользователя в текущей базе данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-permissions-function-with-statement-permissions"></a>A. Использование функции PERMISSIONS с разрешениями на выполнение инструкций  
 В следующем примере определяется, может ли текущий пользователь выполнить инструкцию `CREATE TABLE`.  
  
```  
IF PERMISSIONS()&2=2  
   CREATE TABLE test_table (col1 INT)  
ELSE  
   PRINT 'ERROR: The current user cannot create a table.';  
```  
  
### <a name="b-using-the-permissions-function-with-object-permissions"></a>Б. Использование функции PERMISSIONS с разрешениями на объекты  
 В следующем примере определяется, может ли текущий пользователь вставить строку данных в таблицу `Address`, находящуюся в базе данных `AdventureWorks2012`.  
  
```  
IF PERMISSIONS(OBJECT_ID('AdventureWorks2012.Person.Address','U'))&8=8   
   PRINT 'The current user can insert data into Person.Address.'  
ELSE  
   PRINT 'ERROR: The current user cannot insert data into Person.Address.';  
```  
  
### <a name="c-using-the-permissions-function-with-grantable-permissions"></a>В. Использование функции PERMISSIONS с разрешениями на выполнение инструкции GRANT  
 В следующем примере определяется, может ли текущий пользователь предоставить разрешение INSERT для таблицы `Address`, находящейся в базе данных `AdventureWorks2012`, другому пользователю.  
  
```  
IF PERMISSIONS(OBJECT_ID('AdventureWorks2012.Person.Address','U'))&0x80000=0x80000  
   PRINT 'INSERT on Person.Address is grantable.'  
ELSE  
   PRINT 'You may not GRANT INSERT permissions on Person.Address.';  
```  
  
## <a name="see-also"></a>См. также:  
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [OBJECT_ID (Transact-SQL)](../../t-sql/functions/object-id-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_helprotect (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
