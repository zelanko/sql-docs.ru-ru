---
title: APPLOCK_MODE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4544cc4f0a4d7c1d6d33e1f71bde4b55c09a59c9
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68040358"
---
# <a name="applock_mode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эта функция возвращает режим блокировки, полученный владельцем блокировки на конкретный ресурс приложения. Функция блокировки приложения APPLOCK_MODE действует в текущей базе данных. База данных является областью блокировок приложений.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Аргументы  
'*database_principal*'  
Пользователь, роль или роль приложения, которым могут быть предоставлены разрешения на доступ к объектам базы данных. Для успешного вызова функции вызывающий ее объект должен быть членом предопределенной роли базы данных *database_principal*, dbo или db_owner.
  
'*resource_name*'  
Имя ресурса блокировки, указанное клиентским приложением. Приложение должно гарантировать уникальность имени ресурса. Указанное имя внутренне хэшируется в значение, которое может быть сохранено в диспетчере блокировок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Аргумент *resource_name* имеет тип **nvarchar(255)** и не имеет значения по умолчанию. Аргумент *resource_name* сравнивается в двоичном режиме с учетом регистра символов независимо от параметров сортировки текущей базы данных.
  
'*lock_owner*'  
Владелец блокировки, которая имеет значение *lock_owner* на момент запроса блокировки. Аргумент *lock_owner* имеет тип **nvarchar(32)** и может иметь значение **Transaction** (по умолчанию) или **Session**.
  
## <a name="return-types"></a>Типы возвращаемых данных
**nvarchar(32)**
  
## <a name="return-value"></a>Возвращаемое значение
Возвращает режим блокировки, полученный владельцем блокировки на конкретный ресурс приложения. Режим блокировки может принимать следующие значения:
  
||||  
|-|-|-|  
|**NoLock**|**Update**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**Shared**|**Монопольно**||  
  
* Этот режим блокировки представляет собой сочетание других режимов и не может быть явным образом получен процедурой sp_getapplock.
  
## <a name="function-properties"></a>Свойства функции
**Nondeterministic**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>Примеры  
Два пользователя (пользователь А и пользователь Б) с отдельными сеансами запускают приведенную ниже последовательность инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
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
  
## <a name="see-also"></a>См. также раздел
[APPLOCK_TEST (Transact-SQL)](../../t-sql/functions/applock-test-transact-sql.md)  
[sp_getapplock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  
