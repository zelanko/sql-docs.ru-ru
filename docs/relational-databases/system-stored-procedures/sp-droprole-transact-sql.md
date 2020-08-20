---
description: sp_droprole (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a909a672680428cd5cca761945a0443ae5a1630c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474283"
---
# <a name="sp_droprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет роль базы данных из текущей базы данных.  
  
> [!IMPORTANT]  
>  В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **sp_droprole** был ЗАМЕНЕН инструкцией DROP ROLE. **sp_droprole** включается только для обеспечения совместимости с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и может не поддерживаться в будущем выпуске.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'` Имя роли базы данных, удаляемой из текущей базы данных. *Role* имеет тип **sysname**и не имеет значения по умолчанию. *роль* уже должна существовать в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Комментарии  
 С помощью **sp_droprole**можно удалять только роли базы данных.  
  
 Роль базы данных, содержащая членов, не может быть удалена. Прежде чем удалить роли базы данных, необходимо удалить всех ее членов. Чтобы удалить пользователей из роли, используйте **sp_droprolemember**. Если какие-либо пользователи все еще являются членами роли, **sp_droprole** отображает эти члены.  
  
 Невозможно удалить фиксированные роли и **общую** роль.  
  
 Роль не может быть удалена, если ей принадлежат какие-либо защищаемые объекты. Перед удалением роли приложения, которой принадлежат защищаемые объекты, следует сначала перенести данные о принадлежности защищаемых объектов или удалить эти объекты. Для смены владельца объектов, которые не должны удаляться, используйте инструкцию ALTER AUTHORIZATION.  
  
 **sp_droprole** не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL на роль.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как удаляется роль приложения `Sales`.  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [УДАЛИТЬ роль &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
