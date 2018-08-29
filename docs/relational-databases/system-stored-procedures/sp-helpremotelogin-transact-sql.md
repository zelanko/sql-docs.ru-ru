---
title: sp_helpremotelogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0dc7cdc8e647adf1d8ea5e4e2903509c16a2f62
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033377"
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
 [ @remoteserver **=** ] **"***remoteserver***"**  
 Удаленный сервер, об удаленном имени входа которого возвращаются сведения. *удаленный сервер* — **sysname**, значение по умолчанию NULL. Если *remoteserver* является не указан, возвращаются сведения обо всех удаленных серверах, определенных на локальном сервере.  
  
 [ @remotename **=** ] **"***remote_name***"**  
 Конкретное удаленное имя входа на удаленном сервере. *remote_name* — **sysname**, значение по умолчанию NULL. Если *remote_name* не указан, определенные сведения обо всех удаленных пользователях для *remoteserver* возвращается.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|сервер|**sysname**|Имя удаленного сервера, определенного на локальном сервере.|  
|local_user_name|**sysname**|Имя входа на локальном сервере, с которым сопоставлены удаленные имена входа.|  
|remote_user_name|**sysname**|Имя входа на удаленном сервере, который сопоставляется local_user_name.|  
|параметры|**sysname**|Доверенное = Удаленное имя входа не нуждается в подтверждении паролем при установке соединения с локальным сервером из удаленного сервера.<br /><br /> Не доверенное (или пустое) = Для подтверждения удаленного имени входа запрашивается пароль при установке соединения с локальным сервером из удаленного сервера.|  
  
## <a name="remarks"></a>Примечания  
 Список имен удаленных серверов, определенных на локальном сервере с помощью процедуры sp_helpserver.  
  
## <a name="permissions"></a>Разрешения  
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
  
## <a name="see-also"></a>См. также  
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
