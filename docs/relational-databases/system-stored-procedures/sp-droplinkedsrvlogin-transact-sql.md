---
title: sp_droplinkedsrvlogin (Transact-SQL) | Документы Microsoft
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
- sp_droplinkedsrvlogin_TSQL
- sp_droplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplinkedsrvlogin
ms.assetid: 75a4a040-72d5-4d29-8304-de0aa481ad4b
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2e33633f7ac76fd58db3fba0da141d426de14e97
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spdroplinkedsrvlogin-transact-sql"></a>sp_droplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет существующее сопоставление между именем входа на локальном сервере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и именем входа на связанном сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droplinkedsrvlogin [ @rmtsrvname= ] 'rmtsrvname' ,   
   [ @locallogin= ] 'locallogin'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rmtsrvname =** ] **"***серверу rmtsrvname***"**  
 Имя связанного сервера, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяется сопоставление имен входа. *серверу rmtsrvname* — **sysname**, не имеет значения по умолчанию. *серверу rmtsrvname* должен уже существовать.  
  
 [  **@locallogin =** ] **"***locallogin***"**  
 — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Входа на локальном сервере, сопоставленный со связанным сервером *серверу rmtsrvname*. *locallogin* — **sysname**, не имеет значения по умолчанию. Сопоставление для *locallogin* для *серверу rmtsrvname* должен уже существовать. Если значение равно NULL, сопоставление по умолчанию созданные **sp_addlinkedserver**, который сопоставляет все имена входа на локальном сервере с именами входа на связанном сервере будет удален.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Если локальный сервер существующее отображение для имени входа удаляется, использует сопоставление по умолчанию, созданные **sp_addlinkedserver** при подключении к связанному серверу от имени этого имени входа. Чтобы изменить сопоставление по умолчанию, используйте **sp_addlinkedsrvlogin**.  
  
 Если сопоставление по умолчанию также удалено, только имена входа, которые явно задавали сопоставление имени входа к связанному серверу с помощью **sp_addlinkedsrvlogin**, можно получить доступ к связанному серверу.  
  
 **sp_droplinkedsrvlogin** не может выполняться в рамках пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-removing-the-login-mapping-for-an-existing-user"></a>A. Удаление отображения имени входа для существующего пользователя  
 Следующий пример удаляет отображение для имени входа `Mary` с локального сервера на связанный сервер `Accounts`. Имя входа `Mary` использует отображение имени входа по умолчанию.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', 'Mary';  
```  
  
### <a name="b-removing-the-default-login-mapping"></a>Б. Удаление отображения по умолчанию для имени входа  
 Следующий пример удаляет отображение по умолчанию для имени входа, созданного с помощью выполнения процедуры `sp_addlinkedserver` на связанном сервере `Accounts`.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', NULL;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
