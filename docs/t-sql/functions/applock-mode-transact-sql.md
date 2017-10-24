---
title: "APPLOCK_MODE (Transact-SQL) | Документы Microsoft"
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
- APPLOCK_MODE_TSQL
- APPLOCK_MODE
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- APPLOCK_MODE function
ms.assetid: e43d4917-77f1-45cc-b231-68ba7fee3385
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ceec0a5465187e1b470bd9eb8b1039a5b3d60aae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="applockmode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает режим блокировки, полученный владельцем блокировки на конкретный ресурс приложения. APPLOCK_MODE представляет собой функцию блокировки приложения, работающую в текущей базе данных. Областью блокировок приложений является база данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Аргументы  
"*database_principal*"  
Пользователь, роль или роль приложения, которым могут быть предоставлены разрешения на доступ к объектам базы данных. Вызывающий эту функцию участник должен быть членом *database_principal*, dbo или db_owner предопределенной роли базы данных для успешного вызова этой функции.
  
"*resource_name*"  
Имя ресурса блокировки, указанное клиентским приложением. Приложение должно гарантировать уникальность имени ресурса. Указанное имя внутренне хэшируется в значение, которое может быть сохранено в диспетчере блокировок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name*— **nvarchar(255)** без значения по умолчанию. *resource_name* сравнивается в двоичном с учетом регистра, независимо от параметров сортировки текущей базы данных.
  
"*lock_owner*"  
Владелец данной блокировки, который является *lock_owner* значение при запросе блокировки. *lock_owner* — **nvarchar(32)**, а значение может быть либо **транзакции** (по умолчанию) или **сеанса**.
  
## <a name="return-types"></a>Возвращаемые типы
**nvarchar(32)**
  
## <a name="return-value"></a>Возвращаемое значение
Возвращает режим блокировки, полученный владельцем блокировки на конкретный ресурс приложения. Режим блокировки может принимать следующие значения.
  
||||  
|-|-|-|  
|**NoLock**|**Update**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**Общие**|**Монопольно**||  
  
*Этот режим блокировки представляет собой сочетание других режимов и не может быть явным образом получен при помощи процедуры sp_getapplock.
  
## <a name="function-properties"></a>Свойства функции
**Недетерминированные**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>Примеры  
Два пользователя (пользователь А и пользователь Б) с отдельными сеансами запускают следующую последовательность инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
Пользователь А запускает:
  
```sql
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result=sp_getapplock  
    @DbPrincipal='public',  
    @Resource='Form1',  
    @LockMode='Shared',  
    @LockOwner='Transaction';  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
GO  
```  
  
Затем пользователь Б запускает:
  
```sql
Use AdventureWorks2012;  
GO  
BEGIN TRAN;  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
--Result set: NoLock  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Shared', 'Transaction');  
--Result set: 1 (Lock is grantable.)  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: 0 (Lock is not grantable.)  
GO  
```  
  
Затем пользователь А запускает:
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
Затем пользователь Б запускает:
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
Затем оба пользователя (А и Б) запускают:
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>См. также:
[APPLOCK_TEST &#40; Transact-SQL &#41;](../../t-sql/functions/applock-test-transact-sql.md)  
[процедура sp_getapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  

