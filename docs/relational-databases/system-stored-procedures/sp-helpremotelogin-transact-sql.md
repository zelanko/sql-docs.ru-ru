---
title: "sp_helpremotelogin (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs: TSQL
helpviewer_keywords: sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b34842bc6265d9a1615cb1f2e45d727b257a5c90
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpremotelogin-transact-sql"></a>sp_helpremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об удаленных именах входа для конкретного удаленного сервера либо для всех удаленных серверов, определенных на локальном сервере.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Используйте вместо этого связанные серверы и хранимые процедуры связанных серверов.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @remoteserver  **=**  ] **"***remoteserver***"**  
 Удаленный сервер, об удаленном имени входа которого возвращаются сведения. *удаленный сервер* — **sysname**, значение по умолчанию NULL. Если *remoteserver* — не указано, возвращаются сведения обо всех удаленных серверах, определенных на локальном сервере.  
  
 [ @remotename  **=**  ] **"***remote_name***"**  
 Конкретное удаленное имя входа на удаленном сервере. *remote_name* — **sysname**, значение по умолчанию NULL. Если *remote_name* не указан, определенные сведения обо всех удаленных пользователях для *remoteserver* возвращается.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|сервер|**sysname**|Имя удаленного сервера, определенного на локальном сервере.|  
|local_user_name|**sysname**|Имя входа на локальном сервере, с которым сопоставлены удаленные имена входа.|  
|remote_user_name|**sysname**|Имя входа на удаленном сервере, который сопоставляется local_user_name.|  
|параметры|**sysname**|Доверенное = Удаленное имя входа не нуждается в подтверждении паролем при установке соединения с локальным сервером из удаленного сервера.<br /><br /> Не доверенное (или пустое) = Для подтверждения удаленного имени входа запрашивается пароль при установке соединения с локальным сервером из удаленного сервера.|  
  
## <a name="remarks"></a>Замечания  
 Чтобы получить список имен удаленных серверов, определенных на локальном сервере, используйте sp_helpserver.  
  
## <a name="permissions"></a>Permissions  
 Разрешения не проверяются.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-reporting-help-on-a-single-server"></a>A. Получение справки по одиночному серверу  
 В следующем примере отображаются сведения обо всех удаленных пользователях на удаленном сервере `Accounts`.  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>Б. Получение справки по всем удаленным пользователям  
 В следующем примере отображаются сведения обо всех удаленных пользователях на всех удаленных серверах, известных локальному серверу.  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_addremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Хранимая процедура sp_remoteoption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
