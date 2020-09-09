---
description: sp_releaseapplock (Transact-SQL)
title: sp_releaseapplock (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs:
- TSQL
helpviewer_keywords:
- sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ec619fc8053b735e952b2577f6cdee5d4647e652
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538674"
---
# <a name="sp_releaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Снимает блокировку ресурса приложения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @Resource =] "*resource_name*"  
 Имя ресурса блокировки, указанное клиентским приложением. Приложение должно убедиться в уникальности ресурса. Указанное имя внутренне хэшируется в значение, которое может быть сохранено в диспетчере блокировок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* имеет тип **nvarchar (255)** и не имеет значения по умолчанию. *resource_name* является двоичным по сравнению с учетом регистра, независимо от параметров сортировки текущей базы данных.  
  
 [ @LockOwner =] "*lock_owner*"  
 Владелец блокировки, которая имеет значение *lock_owner* на момент запроса блокировки. Аргумент *lock_owner* имеет тип **nvarchar(32)**. Значением может быть **Transaction** (по умолчанию) или **Session**. Если *lock_owner* значение — **Transaction**, по умолчанию или указывается явным образом, sp_getapplock необходимо выполнять в рамках транзакции.  
  
 [ @DbPrincipal =] "*database_principal*"  
 Пользователь, роль или роль приложения, которые имеют разрешения на объект базы данных. Вызывающая функция должна быть членом предопределенной роли базы данных *database_principal*, dbo или db_owner, чтобы успешно вызвать функцию. Значение по умолчанию: public.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 \>= 0 (успешное завершение) или < 0 (сбой)  
  
|Значение|Результат|  
|-----------|------------|  
|0|Блокировка успешно снята.|  
|— 999|Сигнализирует об ошибке проверки параметра или о другой ошибке вызова процедуры.|  
  
## <a name="remarks"></a>Примечания  
 Если приложение вызывает процедуру sp_getapplock несколько раз для одного и того же ресурса блокировки, то процедура sp_releaseapplock должна вызываться такое же количество раз для снятия блокировки.  
  
 При отключении сервера вне зависимости от причины отключения освобождаются все блокировки.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере освобождается блокировка ресурса `Form1`, связанная с текущей транзакцией в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [APPLOCK_MODE &#40;Transact-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;Transact-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_getapplock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  
