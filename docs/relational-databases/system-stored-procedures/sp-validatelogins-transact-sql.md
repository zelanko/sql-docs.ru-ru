---
title: sp_validatelogins (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_validatelogins
- sp_validatelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validatelogins
ms.assetid: 6ac52e21-e20d-469b-ad40-5aa091e06b61
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99463e2d5e22acbdb69458f2119fc7410492621b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spvalidatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
|**SID**|**varbinary(85)**|Идентификатор защиты (SID) пользователя или группы Windows.|  
|**Имя входа для NT**|**sysname**|Имя пользователя или группы Windows.|  
  
## <a name="remarks"></a>Замечания  
 Если потерянный участник уровня сервера владеет пользователем базы данных, этот пользователь должен быть удален, прежде чем станет возможным удаление потерянного участника. Чтобы удалить пользователя базы данных, используйте [DROP USER](../../t-sql/statements/drop-user-transact-sql.md). Если участник уровня сервера владеет защищаемыми сущностями в базе данных, владение этими сущностями должно быть передано другому участнику или их следует удалить. Для передачи владения такими сущностями базы данных, используйте [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 Чтобы удалить сопоставление пользователей и групп, которые больше не существуют Windows, используйте [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** или **securityadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере отображаются пользователи и группы Windows, которых больше не существует, но которым все еще предоставлен доступ к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Хранимые процедуры безопасности (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [УДАЛИТЬ пользователя & #40; Transact-SQL & #41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN & #40; Transact-SQL & #41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
