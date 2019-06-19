---
title: процедура sp_syspolicy_repair_policy_automation (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_repair_policy_automation
- sp_syspolicy_repair_policy_automation_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_repair_policy_automation
ms.assetid: d81682e3-2444-4d66-ad00-1cf628632e8b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 67e73bd412299910b0fdd0927466ea953c7991fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63005860"
---
# <a name="spsyspolicyrepairpolicyautomation-transact-sql"></a>sp_syspolicy_repair_policy_automation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Исправляет автоматизацию политик в управлении на основе политик. Например, с помощью этой хранимой процедуры можно исправлять триггеры и задания, сопоставленные с политиками, которые настраиваются для использования режимов оценки «По расписанию» и «При изменении».  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_repair_policy_automation  
```  
  
## <a name="arguments"></a>Аргументы  
 Данная хранимая процедура не имеет параметров.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_syspolicy_repair_policy_automation должна выполняться в контексте системной базы данных msdb.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможно повышение учетных данных: Пользователи с ролью PolicyAdministratorRole могут создавать триггеры сервера и планировать выполнение политик, влияющих на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере исправляется автоматизации политики.  
  
```  
EXEC msdb.dbo.sp_syspolicy_repair_policy_automation;  
  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры управления на основе политик &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)  
  
  
