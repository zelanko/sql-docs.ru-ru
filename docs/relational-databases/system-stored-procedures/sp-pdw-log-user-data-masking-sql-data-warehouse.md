---
title: sp_pdw_log_user_data_masking (хранилище данных SQL) | Документация Майкрософт
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
ms.openlocfilehash: 18798dece1c801ad0cc4854b7fccc15529a56d5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056448"
---
# <a name="sp_pdw_log_user_data_masking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Используйте **sp_pdw_log_user_data_masking** , чтобы включить Маскирование данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] в журналах действий. Маскирование данных пользователя влияет на инструкции во всех базах данных на устройстве.  
  
> [!IMPORTANT]  
>  Журналы [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] действий, затрагиваемые **sp_pdw_log_user_data_masking** , являются [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] определенными журналами действий. **sp_pdw_log_user_data_masking** не влияет на журналы транзакций базы данных или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журналы ошибок.  
  
 **Фон:** В журналах действий [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] конфигурации по умолчанию [!INCLUDE[tsql](../../includes/tsql-md.md)] содержит полные инструкции и в некоторых случаях может содержать данные пользователей, содержащиеся в таких операциях, как **INSERT**, **Update**и **SELECT** . В случае возникновения проблемы на устройстве это позволяет анализировать условия, вызвавшие проблему, без необходимости воспроизведения проблемы. Чтобы предотвратить запись данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, клиенты могут включить маскировку данных пользователя с помощью этой хранимой процедуры. Инструкции по-прежнему будут записываться [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] в журналы действий, но все литералы в инструкциях, которые могут содержать пользовательские данные, будут замаскированы. заменено некоторыми предопределенными константными значениями.  
  
 Если на устройстве включено прозрачное шифрование данных, Маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий включается автоматически.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Параметры  
`[ @masking_mode = ] masking_mode`Определяет, включено ли маскирование прозрачных данных пользователя журнала шифрования данных. *masking_mode* имеет **тип int**и может принимать одно из следующих значений:  
  
-   0 = отключено, данные пользователя отображаются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий.  
  
-   1 = включено, в журналах [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] действий отображаются операторы данных пользователя, но данные пользователя маскируются.  
  
-   2 = инструкции, содержащие пользовательские данные, не записываются в журналы [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] действий.  
  
 При **sp_pdw_ log_user_data_masking** без параметров возвращается текущее состояние маскировки данных пользователя журнала TDE на устройстве в качестве скалярного результирующего набора.  
  
## <a name="remarks"></a>Remarks  
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
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_pdw_database_encryption хранилища данных SQL &#40;&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys хранилища данных SQL &#40;&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
