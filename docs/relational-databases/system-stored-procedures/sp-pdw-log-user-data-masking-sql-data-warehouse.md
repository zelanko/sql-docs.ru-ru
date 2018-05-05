---
title: sp_pdw_log_user_data_masking (хранилище данных SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-data-warehouse
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 27b303f1e78826e74fb94f254a0c2e3692fbef7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Используйте **sp_pdw_log_user_data_masking** для включения маскирования в данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий. Маскирование данных пользователя влияет на инструкции для всех баз данных на устройстве.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Затронутых журналы действий **sp_pdw_log_user_data_masking** некоторые [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий. **sp_pdw_log_user_data_masking** не влияет на журналов транзакций базы данных, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журналы ошибок.  
  
 **Фон:** в конфигурации по умолчанию [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий содержат полные [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций и может в некоторых случаях включает данные пользователей, содержащихся в операции, такие как **вставить**,  **ОБНОВЛЕНИЕ**, и **ВЫБЕРИТЕ** инструкции. При возникновении проблемы на устройстве это позволяет анализа условий, которым она вызвана без необходимости воспроизвести проблему. Чтобы предотвратить запись для пользовательских данных [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, которые клиенты могут выбрать включение маскирование данных пользователя с помощью этой хранимой процедуры. Инструкции по-прежнему должны записываться в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, но все литералы в инструкциях, может содержать данные пользователя будут замаскированы; заменить некоторые предопределенные значения констант.  
  
 При включении прозрачного шифрования данных на устройстве маскировки данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий включается автоматически.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Параметры  
 [  **@masking_mode=** ] *masking_mode*  
 Определяет, включено ли прозрачное шифрование журнала пользователях маскировки. *masking_mode* — **int**, и может принимать одно из следующих значений:  
  
-   0 = отключено, пользователь, данные отображаются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
-   1 = включено, пользователь инструкции данных отображаются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] маскируются журналы действий, но данные пользователя.  
  
-   2 = инструкции, содержащий данные пользователя не записываются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
 Выполнение **sp_pdw_ log_user_data_masking** без параметров возвращает текущее состояние маскирования данных пользовательского журнала прозрачное шифрование данных на устройстве как скалярные результирующий набор.  
  
## <a name="remarks"></a>Замечания  
 Маскирования в данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналах действий замены литералы с предопределенные значения констант в **ВЫБЕРИТЕ** и инструкций DML, как они могут содержать пользовательские данные. Установка *masking_mode* 1 не устанавливает маску метаданные, такие как имена столбцов или таблиц. Установка *masking_mode* 2 удаляет инструкций с метаданными, например имена столбцов или таблиц.  
  
 Данные пользователя маскировки в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий реализуется следующим образом:  
  
-   Прозрачное шифрование данных и данных пользователя маскировки в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий по умолчанию отключены. Операторы не будет скрываться автоматически, если база данных не требуется шифрование на устройстве.  
  
-   Включение прозрачного шифрования данных на устройстве автоматически включает маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
-   Отключение прозрачное шифрование данных не влияет на данные пользователя маскировки в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
-   Можно явным образом включить маскирования в данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий с помощью **sp_pdw_log_user_data_masking** процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли базы данных или **CONTROL SERVER** разрешение.  
  
## <a name="example"></a>Пример  
 В следующем примере включается маскировки на устройстве данных пользовательского журнала прозрачного шифрования данных.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_pdw_database_encryption &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
