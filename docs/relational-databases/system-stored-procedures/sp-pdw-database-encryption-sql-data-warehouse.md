---
title: sp_pdw_database_encryption (хранилище данных SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: da83081e3d5eb24a38424e6bdafc68014f6a490d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Используйте **sp_pdw_database_encryption** Чтобы включить прозрачное шифрование данных для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] устройства. Когда **sp_pdw_database_encryption** равно 1, используйте **инструкции ALTER DATABASE** инструкции для шифрования базы данных с помощью прозрачного шифрования данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Параметры  
 [  **@enabled=** ] *включена*  
 Определяет, включено ли прозрачное шифрование данных. *включить* — **int**, и может принимать одно из следующих значений:  
  
-   0 = Отключено  
  
-   1 = Включено  
  
 Выполнение **sp_pdw_database_encryption** без параметров возвращает текущее состояние прозрачное шифрование данных на устройстве как набор скалярный результат: 0 — отключено, или 1 для включена.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 При включении прозрачного шифрования данных с помощью **sp_pdw_database_encryption**, база данных tempdb удалены, заново и зашифрованы. По этой причине прозрачного шифрования данных невозможно активировать на устройство, пока существуют другие активные сеансы с помощью базы данных tempdb. Включение или отключение прозрачное шифрование данных на устройство имеет действие, которое изменяет состояние устройства, в большинстве случаев должно выполнить один раз во время существования устройства и должна быть выполнена при отсутствии трафика на устройстве.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **sysadmin** предопределенной роли базы данных или **CONTROL SERVER** разрешение.  
  
## <a name="example"></a>Пример  
 Следующий пример включает прозрачное шифрование данных на устройстве.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
