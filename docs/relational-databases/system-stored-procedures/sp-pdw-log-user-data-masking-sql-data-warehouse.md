---
title: sp_pdw_log_user_data_masking (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 16de9489583cce2e696a94c75c7e5fd3ac1c0fe1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993716"
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Используйте **sp_pdw_log_user_data_masking** для включения маскирования в данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий. Маскирование данных пользователя влияет на инструкции для всех баз данных на устройстве.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Журналы действий влияет **sp_pdw_log_user_data_masking** уверены [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий. **sp_pdw_log_user_data_masking** не влияет на журналах транзакций базы данных, или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журналы ошибок.  
  
 **Фон:** в конфигурации по умолчанию [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий содержат полную [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций и может в некоторых случаях включают пользовательские данные, содержащиеся в операциях, таких как **вставить**,  **ОБНОВЛЕНИЕ**, и **ВЫБЕРИТЕ** инструкций. При возникновении проблемы на устройстве это позволяет анализа условий, которые не нужно воспроизвести проблему их причиной. Чтобы не допустить данные пользователя, записываемый [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, которые клиенты могут выбрать включение маскирование данных пользователя с помощью этой хранимой процедуры. Инструкции по-прежнему должны записываться в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий, но все литералы в инструкциях, может содержать данные пользователя будут замаскированы; заменить некоторые предопределенные константы.  
  
 При включении прозрачного шифрования данных на устройстве маскирования данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий включается автоматически.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Параметры  
 [  **@masking_mode=** ] *masking_mode*  
 Определяет, включено ли прозрачное шифрование журнала пользователя данных маскирование. *masking_mode* — **int**, и может принимать одно из следующих значений:  
  
-   0 = отключено, пользователь, данные появляются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
-   1 = включено, пользователь, инструкции данных отображаются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] маскировки журналы действий, но данные пользователя.  
  
-   2 =-операторы, содержащий данные пользователя, не записываются в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
 Выполнение **sp_pdw_ log_user_data_masking** без параметров возвращает текущее состояние маскирования данных пользователя для прозрачного шифрования данных журнала на устройстве как скалярные результирующий набор.  
  
## <a name="remarks"></a>Примечания  
 Маскирования в данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] замены литералы журналы действий с помощью предопределенных констант в **ВЫБЕРИТЕ** и инструкций DML, так как они могут содержать данные пользователя. Установка *masking_mode* 1 не устанавливает маску метаданные, такие как имена столбцов или таблиц. Установка *masking_mode* 2 удаляет инструкций с метаданными, такие как имена столбцов или таблиц.  
  
 Данные пользователя, маски в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий реализуется следующим образом:  
  
-   Прозрачное шифрование данных и данных пользователя маскирования в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий по умолчанию отключены. Операторы не будет скрываться автоматически, если на устройстве не включено шифрование базы данных.  
  
-   Включение прозрачного шифрования данных на устройстве автоматически включает маскирование данных пользователя в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
-   Отключение TDE не влияет на данные пользователя, маски в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий.  
  
-   Вы можете явным образом включить маскирования в данных пользователя [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] журналы действий с помощью **sp_pdw_log_user_data_masking** процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли базы данных или **CONTROL SERVER** разрешение.  
  
## <a name="example"></a>Пример  
 В следующем примере включается данные пользователя прозрачного шифрования данных журнала, маскирование на устройстве.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_pdw_database_encryption &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
