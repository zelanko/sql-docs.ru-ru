---
title: "APPLOCK_TEST (Transact-SQL) | Документы Microsoft"
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
- APPLOCK_TEST_TSQL
- APPLOCK_TEST
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- APPLOCK_TEST function
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- testing application locks
ms.assetid: 4ea33d04-f8e9-46ff-ae61-985bd3eaca2c
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a272abaccb41653c9b1b0569738b74905e93e5c9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="applocktest-transact-sql"></a>APPLOCK_TEST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает сведения о том, может ли быть предоставлена блокировка конкретного ресурса приложения для указанного владельца блокировки без запроса на блокировку. APPLOCK_TEST является функцией блокировки приложения и действует в текущей базе данных. Областью блокировок приложений является база данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
APPLOCK_TEST ( 'database_principal' , 'resource_name' , 'lock_mode' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Аргументы  
**"** *database_principal* **"**  
Пользователь, роль или роль приложения, которым могут быть предоставлены разрешения на доступ к объектам базы данных. Вызывающий эту функцию участник должен быть членом *database_principal*, **dbo**, или **db_owner** предопределенной роли базы данных для успешного вызова этой функции.
  
**"** *resource_name* **"**  
Имя ресурса блокировки, указанное клиентским приложением. Приложение должно убедиться в уникальности ресурса. Указанное имя внутренне хэшируется в значение, которое может быть сохранено в диспетчере блокировок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name*— **nvarchar(255)** без значения по умолчанию. *resource_name* сравнивается с учетом регистра, независимо от параметров сортировки текущей базы данных.
  
**"** *lock_mode* **"**  
Надо ли получить режим блокировки для указанного ресурса. *lock_mode* — **nvarchar(32)** и нет значения по умолчанию. Значение может быть одним из следующих: **Shared**, **обновление**, **IntentShared**, **IntentExclusive**, **монопольного** .
  
**"** *lock_owner* **"**  
Владелец данной блокировки, который является *lock_owner* значение при запросе блокировки. *lock_owner* — **nvarchar(32)**. Значение может быть **транзакции** (по умолчанию) или **сеанса**. Если по умолчанию или **транзакции** явно не указан, APPLOCK_TEST должно выполняться в рамках транзакции.
  
## <a name="return-types"></a>Возвращаемые типы
**smallint**
  
## <a name="return-value"></a>Возвращаемое значение
Возвращает 0, когда блокировка не может быть предоставлена указанному владельцу, и возвращает 1, если блокировка может быть предоставлена.
  
## <a name="function-properties"></a>Свойства функции
**Недетерминированные**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>Примеры  
В следующем примере два пользователя (**пользователь A** и **пользователь Б**) с отдельными сеансами запускают следующую последовательность [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.
  
**Пользователь А** выполняется:
  
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
  
**Пользователь Б** запускает:
  
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
  
**Пользователь А** запускает:
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
**Пользователь Б** запускает:
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
**Пользователь А** и **пользователь Б** , а затем запустите оба:
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>См. также:
[APPLOCK_MODE &#40; Transact-SQL &#41;](../../t-sql/functions/applock-mode-transact-sql.md)  
[процедура sp_getapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  

