---
title: "РАЗРЕШЕНИЯ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3dfe09c059d2d1e3b41f7cc21de1d011c582be44
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="permissions-transact-sql"></a>PERMISSIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает битовую карту, указывающую разрешения на инструкции, объекты и столбцы для текущего пользователя.  
  
 **Важные** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] используйте [fn_my_permissions](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md) и [Has_Perms_By_Name](../../t-sql/functions/has-perms-by-name-transact-sql.md) вместо него. Постоянное использование функции PERMISSIONS может привести к понижению производительности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PERMISSIONS ( [ objectid [ , 'column' ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *ObjectID*  
 Идентификатор защищаемого объекта. Если *objectid* — не указано, значение битовой карты содержит разрешения на инструкции для текущего пользователя; в противном случае битовая карта содержит разрешения на защищаемый объект для текущего пользователя. Указанный защищаемый объект должен находиться в текущей базе данных. Используйте [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md) функцию, чтобы определить *objectid* значение.  
  
 **"** *столбца* **"**  
 Необязательное имя столбца, для которого возвращаются данные о разрешениях. Столбец должен быть допустимым именем столбца в таблице, указанной аргументом *objectid*.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="remarks"></a>Замечания  
 С помощью функции PERMISSIONS можно определить, имеет ли текущий пользователь разрешения, необходимые для выполнения инструкции или предоставления разрешения другому пользователю с помощью инструкции GRANT.  
  
 Возвращаемые данные о разрешениях представляют собой 32-разрядную битовую карту.  
  
 Младшие 16 разрядов отражают разрешения, предоставленные пользователю, и разрешения, применяемые к группам Windows и предопределенным ролям сервера, членство в которых имеет текущий пользователь. Например, значение 66 (шестнадцатеричное значение 0x42), если не *objectid* указан, то указывает, что у пользователя есть разрешение на выполнение CREATE TABLE (десятичное значение 2) и инструкции BACKUP DATABASE (десятичное значение 64).  
  
 Старшие 16 разрядов отражают разрешения, которые пользователь может предоставить другим пользователям с помощью инструкции GRANT. Старшие 16 разрядов интерпретируются точно так же, как и младшие 16 разрядов, описанные в следующих таблицах, но они сдвинуты влево на 16 разрядов (умножены на 65536). Например, 0x8 (десятичное значение 8) — бит, который отражает разрешение INSERT, когда *objectid* указано. А 0x80000 (десятичное значение 524288) указывает на возможность предоставления разрешения INSERT с помощью инструкции GRANT, так как 524288 = 8 x 65536.  
  
 Благодаря членству в ролях, пользователь, не имеющий разрешения выполнить инструкцию, может предоставить такое разрешение другому пользователю.  
  
 В следующей таблице показаны битов, используемых для разрешения инструкции (*objectid* не указан).  
  
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
|256|0x100|Зарезервировано|  
  
 В следующей таблице приведены разряды, которым разрешения на объекты, возвращаемые, только если *objectid* указано.  
  
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
  
 В следующей таблице приведены разряды, которым разрешения на объекты уровня столбца, возвращаются, когда оба *objectid* и указанных столбцов.  
  
|Разряд (дес.)|Разряд (шест.)|Разрешение на инструкцию|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT|  
|2|0x2|UPDATE|  
|4|0x4|REFERENCES|  
  
 Если указанный параметр имеет значение NULL или не является допустимым, возвращается значение NULL (например, *objectid* или столбец, который не существует). Битовые значения для неприменимых разрешений (например, разрешение EXECUTE для таблицы, разряды 0x20) не определены.  
  
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
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

