---
title: sp_validatelogins (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_validatelogins
- sp_validatelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validatelogins
ms.assetid: 6ac52e21-e20d-469b-ad40-5aa091e06b61
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 149831d9926161f697c69a893c00784230480940
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723022"
---
# <a name="sp_validatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает сведения о сопоставленных с участниками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователях и группах Windows, которые больше не существуют в среде Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ТРАНСЛЯЦИЮ**|**varbinary(85)**|Идентификатор защиты (SID) пользователя или группы Windows.|  
|**NT Login**|**sysname**|Имя пользователя или группы Windows.|  
  
## <a name="remarks"></a>Примечания  
 Если потерянный участник уровня сервера владеет пользователем базы данных, этот пользователь должен быть удален, прежде чем станет возможным удаление потерянного участника. Чтобы удалить пользователя базы данных, используйте [инструкцию DROP USER](../../t-sql/statements/drop-user-transact-sql.md). Если участник уровня сервера владеет защищаемыми сущностями в базе данных, владение этими сущностями должно быть передано другому участнику или их следует удалить. Чтобы передавать владение защищаемыми объектами базы данных, используйте [инструкцию ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 Чтобы удалить сопоставления пользователей и групп Windows, которые больше не существуют, используйте [инструкцию DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **sysadmin** или **администратора** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере отображаются пользователи и группы Windows, которых больше не существует, но которым все еще предоставлен доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Удаление пользователя &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN &#40;&#41;Transact-SQL](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
