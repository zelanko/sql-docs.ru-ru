---
title: sp_droplinkedsrvlogin (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droplinkedsrvlogin_TSQL
- sp_droplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplinkedsrvlogin
ms.assetid: 75a4a040-72d5-4d29-8304-de0aa481ad4b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3f6df8ac0be9a6bfc8798697ec01e7e5a2c8e3d3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85859838"
---
# <a name="sp_droplinkedsrvlogin-transact-sql"></a>sp_droplinkedsrvlogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет существующее сопоставление между именем входа на локальном сервере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и именем входа на связанном сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droplinkedsrvlogin [ @rmtsrvname= ] 'rmtsrvname' ,   
   [ @locallogin= ] 'locallogin'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rmtsrvname = ] 'rmtsrvname'`Имя связанного сервера, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к которому применяется сопоставление имен входа. *рмтсрвнаме* имеет тип **sysname**и не имеет значения по умолчанию. *рмтсрвнаме* уже должен существовать.  
  
`[ @locallogin = ] 'locallogin'`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Имя входа на локальном сервере с сопоставлением со связанным сервером *рмтсрвнаме*. *локаллогин* имеет тип **sysname**и не имеет значения по умолчанию. Сопоставление для *локаллогин* с *рмтсрвнаме* должно уже существовать. Если значение равно NULL, то сопоставление по умолчанию, созданное **sp_addlinkedserver**, которое сопоставляет все имена входа на локальном сервере с именами входа на связанном сервере, удаляется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 При удалении существующего сопоставления для имени входа локальный сервер использует сопоставление по умолчанию, созданное **sp_addlinkedserver** при подключении к связанному серверу от имени этого имени входа. Чтобы изменить сопоставление по умолчанию, используйте **sp_addlinkedsrvlogin**.  
  
 Если сопоставление по умолчанию также удалено, то к связанному серверу могут быть подключены только имена входа, для которых явно задано сопоставление имени входа со связанным сервером с помощью **sp_addlinkedsrvlogin**.  
  
 невозможно выполнить **sp_droplinkedsrvlogin** из определяемой пользователем транзакции.  
  
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
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
