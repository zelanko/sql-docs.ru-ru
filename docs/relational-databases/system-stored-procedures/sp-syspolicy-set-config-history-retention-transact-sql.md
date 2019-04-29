---
title: процедура sp_syspolicy_set_config_history_retention (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_set_config_history_retention_TSQL
- sp_syspolicy_set_config_history_retention
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_set_config_history_retention
ms.assetid: 2574898a-e724-4447-b96c-ff778471339d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 4f810cc775e79da6d01a2856afb04f80756be68a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000807"
---
# <a name="spsyspolicysetconfighistoryretention-transact-sql"></a>sp_syspolicy_set_config_history_retention (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает число дней, в течение которых хранится журнал выполнения политик для управления на основе политик.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_set_config_history_retention [ @value = ] value  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @value = ] value` — Число дней хранения журнала управления на основе политик. *значение* — **sqlvariant**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_syspolicy_set_config_history_retention должна выполняться в контексте системной базы данных msdb.  
  
 Если *значение* имеет значение 0, журнал не удаляется автоматически.  
  
 Чтобы просмотреть текущее значение срока хранения журнала, выполните следующий запрос:  
  
```  
SELECT current_value FROM msdb.dbo.syspolicy_configuration  
WHERE name = 'HistoryRetentionInDays'  
```  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможно повышение учетных данных: Пользователи с ролью PolicyAdministratorRole могут создавать триггеры сервера и планировать выполнение политик, влияющих на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере устанавливается 28-дневный срок хранения журнала выполнения политик.  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_config_history_retention @value = 28;  
  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры управления на основе политик &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [процедура sp_syspolicy_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  
