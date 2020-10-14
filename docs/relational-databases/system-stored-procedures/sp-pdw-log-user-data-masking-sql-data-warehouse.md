---
description: sp_pdw_log_user_data_masking (Azure синапсе Analytics)
title: sp_pdw_log_user_data_masking (Azure синапсе Analytics) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 87c151558a290f3c06a605de72931c5ee6990f60
ms.sourcegitcommit: 76ab3b57718341c6057613c9bd38cf82fb17786e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92059362"
---
# <a name="sp_pdw_log_user_data_masking-azure-synapse-analytics"></a>sp_pdw_log_user_data_masking (Azure синапсе Analytics)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Используйте **sp_pdw_log_user_data_masking** , чтобы включить Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий. Маскирование данных пользователя влияет на инструкции во всех базах данных на устройстве.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Журналы действий, затрагиваемые **sp_pdw_log_user_data_masking** , являются определенными [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналами действий. **sp_pdw_log_user_data_masking** не влияет на журналы транзакций базы данных или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журналы ошибок.  
  
 **Фон:** В журналах действий конфигурации по умолчанию [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] содержит полные [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции и в некоторых случаях может содержать данные пользователей, содержащиеся в таких операциях, как **INSERT**, **Update**и **SELECT** . В случае возникновения проблемы на устройстве это позволяет анализировать условия, вызвавшие проблему, без необходимости воспроизведения проблемы. Чтобы предотвратить запись данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, клиенты могут включить маскировку данных пользователя с помощью этой хранимой процедуры. Инструкции по-прежнему будут записываться в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, но все литералы в инструкциях, которые могут содержать пользовательские данные, будут замаскированы; заменяются некоторыми предопределенными константными значениями.  
  
 Если на устройстве включено прозрачное шифрование данных, Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий включается автоматически.  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql  
-- Syntax for Azure Synapse Analytics and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```

[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]
  
#### <a name="parameters"></a>Параметры  
`[ @masking_mode = ] masking_mode` Определяет, включено ли маскирование прозрачных данных пользователя журнала шифрования данных. *masking_mode* имеет **тип int**и может принимать одно из следующих значений:  
  
-   0 = отключено, данные пользователя отображаются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий.  
  
-   1 = включено, в журналах действий отображаются операторы данных пользователя, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] но данные пользователя маскируются.  
  
-   2 = инструкции, содержащие пользовательские данные, не записываются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
 При **sp_pdw_ log_user_data_masking** без параметров возвращается текущее состояние маскировки данных пользователя журнала TDE на устройстве в качестве скалярного результирующего набора.  
  
## <a name="remarks"></a>Комментарии  
 Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий позволяет заменить литералы предопределенными константными значениями в инструкциях **SELECT** и DML, так как они могут содержать пользовательские данные. Установка *masking_mode* в значение 1 не маскирует метаданные, такие как имена столбцов или имена таблиц. Если присвоить параметру *masking_mode* значение 2, то инструкции с метаданными, например имена столбцов или имена таблиц, удаляются.  
  
 Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий реализуется следующим образом:  
  
-   TDE и Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий по умолчанию отключены. Инструкции не будут автоматически маскироваться, если шифрование базы данных не включено на устройстве.  
  
-   При включении TDE на устройстве автоматически включается Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий.  
  
-   Отключение TDE не влияет на маскировку данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий.  
  
-   Можно явно включить Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий с помощью **sp_pdw_log_user_data_masking** процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **sysadmin** или разрешение **Control Server** .  
  
## <a name="example"></a>Пример  
 В следующем примере включается Маскирование данных пользователя журнала TDE на устройстве.  
  
```sql  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_pdw_database_encryption &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
