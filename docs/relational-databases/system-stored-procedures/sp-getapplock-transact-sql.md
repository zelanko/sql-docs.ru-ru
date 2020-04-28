---
title: sp_getapplock (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getapplock_TSQL
- sp_getapplock
dev_langs:
- TSQL
helpviewer_keywords:
- application locks
- sp_getapplock
ms.assetid: e1e85908-9f31-47cf-8af6-88c77e6f24c9
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fee963f1b026090a84e58a9b0844fe040f9e9793
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72717253"
---
# <a name="sp_getapplock-transact-sql"></a>sp_getapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Размещает блокировку на ресурсе приложения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_getapplock [ @Resource = ] 'resource_name' ,  
     [ @LockMode = ] 'lock_mode'   
     [ , [ @LockOwner = ] 'lock_owner' ]   
     [ , [ @LockTimeout = ] 'value' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @Resource= ] "*resource_name*"  
 Строка, указывающая имя, которое определяет ресурс блокировки. Приложение должно гарантировать уникальность имени ресурса. Указанное имя внутренне хэшируется в значение, которое может быть сохранено в диспетчере блокировок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* имеет тип **nvarchar (255)** и не имеет значения по умолчанию. Если строка ресурса длиннее **nvarchar (255)**, она будет усечена до **nvarchar (255)**.  
  
 *resource_name* является двоичным по сравнению с учетом регистра, независимо от параметров сортировки текущей базы данных.  
  
> [!NOTE]  
>  После того как произойдет блокировка приложения, только первые 32 символа могут быть получены в виде обычного текста; остаток будет хэширован.  
  
 [ @LockMode= ] "*lock_mode*"  
 Надо ли получить режим блокировки для указанного ресурса. Аргумент *lock_mode* имеет тип **nvarchar(32)** и не имеет значения по умолчанию. Значение может быть любым из следующих: **Shared**, **Update**, **IntentShared**, **IntentExclusive**или **Exclusive**. Дополнительные сведения см. в разделе [режимы блокировки](../sql-server-transaction-locking-and-row-versioning-guide.md#lock_modes).
  
 [ @LockOwner= ] "*lock_owner*"  
 Владелец блокировки, которая имеет значение *lock_owner* на момент запроса блокировки. Аргумент *lock_owner* имеет тип **nvarchar(32)**. Значением может быть **Transaction** (по умолчанию) или **Session**. Если *lock_owner* значение — **Transaction**, по умолчанию или указывается явным образом, sp_getapplock необходимо выполнять в рамках транзакции.  
  
 [ @LockTimeout= ] "*значение*"  
 Значение времени ожидания блокировки (в миллисекундах). Значение по умолчанию совпадает со значением, возвращаемым параметром@LOCK_TIMEOUT@. Чтобы указать, что запрос блокировки должен возвращать код возврата-1, а не ожидать блокировки, когда запрос не может быть предоставлен немедленно, укажите 0.  
  
 [ @DbPrincipal= ] "*database_principal*"  
 Пользователь, роль или роль приложения, которые имеют разрешения на объект базы данных. Вызывающая функция должна быть членом предопределенной роли базы данных *database_principal*, dbo или db_owner для успешного вызова функции. Значение по умолчанию: public.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 \>= 0 (успешное завершение) или < 0 (сбой)  
  
|Значение|Результат|  
|-----------|------------|  
|0|Блокировка была успешно предоставлена в синхронном режиме.|  
|1|Блокировка была предоставлена успешно после снятия других несовместимых блокировок.|  
|-1|Истекло время ожидания запроса блокировки.|  
|-2|Запрос блокировки был отменен.|  
|–3|Запрос блокировки был выбран как жертва взаимоблокировки.|  
|— 999|Указывает ошибку при проверке параметра или другую ошибку вызова.|  
  
## <a name="remarks"></a>Remarks  
 Блокировки, помещенные на ресурс, связаны либо с текущей транзакцией, либо с текущим сеансом. Блокировки, связанные с текущей транзакцией, снимаются, когда транзакция фиксируется или откатывается. Блокировки, связанные с сеансом, освобождаются при выходе из сеанса. Когда сервер завершает работу по какой либо причине, освобождаются все блокировки.  
  
 Ресурс блокировки, созданный процедурой sp_getapplock, создается в текущей базе данных сеанса. Каждый ресурс блокировки определяется объединенными значениями следующих аргументов.  
  
-   Идентификатор базы данных, содержащей ресурс блокировки.  
  
-   Участник базы данных, указанный в параметре @DbPrincipal.  
  
-   Имя блокировки, указанное в параметре @Resource.  
  
 Только элемент участника базы данных, указанного в параметре @DbPrincipal, может запросить блокировки приложений, которые определяют этого участника. Члены ролей dbo и db_owner косвенно являются членами всех ролей.  
  
 Блокировки могут быть сняты явно с помощью процедуры sp_releaseapplock. Если приложение вызывает процедуру sp_getapplock несколько раз для одного и того же ресурса блокировки, то процедура sp_releaseapplock должна вызываться такое же количество раз для снятия блокировки.  При открытии блокировки с владельцем `Transaction` блокировки эта блокировка освобождается при фиксации или откате транзакции.
  
 Если процедура sp_getapplock вызывается несколько раз для одного и того же ресурса блокировки, но режим блокировки, указанный в каком-либо запросе, отличается от существующего режима, на ресурс действует объединение двух режимов блокировки. В большинстве случаев это значит, что режим блокировки повышается до более сильного режима блокировки, до существующего режима или до заново запрашиваемого режима. Более сильный режим блокировки держится до тех пор, пока блокировка не снимается окончательно, даже если вызовы снятия блокировки производятся до этого времени. Например, в следующей последовательности вызовов ресурс удерживается в режиме `Exclusive`, а не в режиме `Shared`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
EXEC @result = sp_releaseapplock @Resource = 'Form1';  
COMMIT TRANSACTION;  
GO  
```  
  
 Взаимоблокировка с блокировкой приложения не откатывает транзакцию, запросившую блокировку приложения. Любой откат, который может потребоваться как результат возвращаемого значения, должен быть сделан вручную. Следовательно, рекомендуется включить в код проверку на ошибки с тем, чтобы в случае возврата определенного значения (например -3) могла быть запущена инструкция ROLLBACK TRANSACTION или предпринято другое действие.  
  
 Например:  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
IF @result = -3  
BEGIN  
    ROLLBACK TRANSACTION;  
END  
ELSE  
BEGIN  
    EXEC @result = sp_releaseapplock @Resource = 'Form1';  
    COMMIT TRANSACTION;  
END;  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует идентификатор текущей базы данных для квалификации ресурса. Поэтому, если процедура sp_getapplock выполняется даже с одинаковыми значениями параметров на разных базах данных, в результате разные блокировки появляются на разных ресурсах.  
  
 Используйте динамическое административное представление sys.dm_tran_locks или системную хранимую процедуру sp_lock, чтобы получить сведения о блокировке, или используйте приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для отслеживания блокировок.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 Следующий пример помещает совмещаемую блокировку, связанную с текущей транзакцией, на ресурс `Form1` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
 В данном примере в качестве участника базы данных задается `dbo`.  
  
```  
BEGIN TRAN;  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'AdventureWorks2012',   
     @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [APPLOCK_MODE &#40;Transact-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;Transact-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_releaseapplock (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)  
  
  
