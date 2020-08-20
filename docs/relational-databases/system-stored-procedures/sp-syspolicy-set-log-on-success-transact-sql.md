---
description: sp_syspolicy_set_log_on_success (Transact-SQL)
title: sp_syspolicy_set_log_on_success (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_set_log_on_success_TSQL
- sp_syspolicy_set_log_on_success
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_set_log_on_success
ms.assetid: 6b33383b-5949-488a-a911-59299a270f46
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: cb17728ab1ac9c063f2198ec707254bf6b2f8eed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485613"
---
# <a name="sp_syspolicy_set_log_on_success-transact-sql"></a>sp_syspolicy_set_log_on_success (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Указывает, записывается ли успешное выполнение политик в журнал политик для управления на основе политик.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_set_log_on_success [ @value = ] value  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @value = ] value` Определяет, регистрируются ли успешные оценки политик. *значение* равно **SQLVARIANT**и может принимать одно из следующих значений:  
  
-   0 или false = успешное выполнение политик не заносится в журнал;  
  
-   1 или true = успешное выполнение политик заносится в журнал.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 Процедура sp_syspolicy_set_log_on_success должна выполняться в контексте системной базы данных msdb.  
  
 Если *параметру value* присвоено значение 0 или false, то регистрируются только оценки политик, не прошедшие проверку.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> **ВАЖНО!** Возможное повышение уровня учетных данных. пользователи в роли PolicyAdministratorRole могут создавать серверные триггеры и планировать выполнение политик, которые могут повлиять на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере включается запись в журнал для успешного выполнения политик.  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_log_on_success @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры управления на основе политик &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  
