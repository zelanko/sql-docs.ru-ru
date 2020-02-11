---
title: sp_pdw_database_encryption_regenerate_system_keys (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
author: ronortloff
ms.author: rortloff
ms.reviewer: ''
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 323b7602fd375bc393828663f1d2c749332dc9ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67463480"
---
# <a name="sp_pdw_database_encryption_regenerate_system_keys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (хранилище данных SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Используйте **sp_pdw_database_encryption_regenerate_system_keys** для смены сертификата и ключа шифрования базы данных для внутренних баз данных, которые шифруются при включении TDE на устройстве. А именно `tempdb`. Это будет успешным, только если включен TDE.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Процедура не имеет параметров.  
  
 Эта процедура должна использоваться, если трафик на устройстве имеет низкий уровень.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **sysadmin** или разрешение **Control Server** .  
  
## <a name="example"></a>Пример  
 В следующем примере повторно создаются ключи шифрования базы данных.  
  
```sql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_pdw_database_encryption хранилища данных SQL &#40;&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking хранилища данных SQL &#40;&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
