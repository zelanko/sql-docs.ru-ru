---
description: xp_enumgroups (Transact-SQL)
title: xp_enumgroups (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_enumgroups_TSQL
- xp_enumgroups
dev_langs:
- TSQL
helpviewer_keywords:
- xp_enumgroups
ms.assetid: 0bd3ed36-e260-469c-a5ff-b033fb9ea59d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ae1a698c5b33780417e74d27f20462b6e1e6e4f5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419288"
---
# <a name="xp_enumgroups-transact-sql"></a>xp_enumgroups (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Предоставляет список локальных групп Microsoft Windows или список глобальных групп, определенных в указанном домене Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_enumgroups [ 'domain_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *domain_name* **"**  
 Имя домена Windows, для которого перечисляется список глобальных групп. Аргумент *domain_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group**|**sysname**|Имя группы Windows|  
|**comment**|**sysname**|Описание группы Windows, предоставленное Windows|  
  
## <a name="remarks"></a>Remarks  
 Если *domain_name* — имя компьютера под управлением Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на котором выполняется экземпляр, или не указано имя домена, **xp_enumgroups** перечисляет локальные группы на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **xp_enumgroups** нельзя использовать, если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает под Windows 98.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** в базе данных **master** или членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере перечисляются группы в домене `sales`.  
  
```  
EXEC xp_enumgroups 'sales';  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
