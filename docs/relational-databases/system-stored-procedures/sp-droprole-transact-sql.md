---
title: sp_droprole (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77c642d6b1574006122af74f0538cdb7ef607535
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620812"
---
# <a name="spdroprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет роль базы данных из текущей базы данных.  
  
> [!IMPORTANT]  
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_droprole** была заменена на инструкцию DROP ROLE. **sp_droprole** включается только для совместимости с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и могут не поддерживаться в будущих выпусках.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@rolename =** ] **"***роли***"**  
 Имя роли базы данных для удаления из текущей базы данных. *роль* — **sysname**, не имеет значения по умолчанию. *роли* уже должен существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Можно удалить только роли базы данных с помощью **sp_droprole**.  
  
 Роль базы данных, содержащая членов, не может быть удалена. Прежде чем удалить роли базы данных, необходимо удалить всех ее членов. Чтобы удалить пользователей из роли, используйте **sp_droprolemember**. Если все пользователи по-прежнему являются членами этой роли, **sp_droprole** отображает их.  
  
 Предопределенные роли и **открытый** роль не может быть удалена.  
  
 Роль не может быть удалена, если ей принадлежат какие-либо защищаемые объекты. Перед удалением роли приложения, которой принадлежат защищаемые объекты, следует сначала перенести данные о принадлежности защищаемых объектов или удалить эти объекты. Для смены владельца объектов, которые не должны удаляться, используйте инструкцию ALTER AUTHORIZATION.  
  
 **sp_droprole** не может выполняться внутри пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL на роль.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как удаляется роль приложения `Sales`.  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE (Transact-SQL)](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
