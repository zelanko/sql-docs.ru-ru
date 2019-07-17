---
title: sp_pdw_database_encryption (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 47d7aca62ddbf2637b54d77171a08817b842555c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008910"
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Используйте **sp_pdw_database_encryption** включить прозрачное шифрование данных на для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] устройства. Когда **sp_pdw_database_encryption** значение 1, используйте **ALTER DATABASE** инструкцию, чтобы зашифровать базу данных с помощью прозрачного шифрования данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Параметры  
`[ @enabled = ] enabled` Определяет, включено ли прозрачное шифрование данных. *включить* — **int**, и может принимать одно из следующих значений:  
  
-   0 = Отключено  
  
-   1 = Включено  
  
 Выполнение **sp_pdw_database_encryption** без параметров возвращает текущее состояние прозрачного шифрования данных на устройстве как скалярные результирующий набор: 0 для отключено, или 1 для включена.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 При включенном TDE с помощью **sp_pdw_database_encryption**, базы данных tempdb удаляется, заново и зашифрованы. По этой причине прозрачного шифрования данных невозможно активировать устройство с поддержкой, пока существуют другие активные сеансы, с помощью базы данных tempdb. Включение или отключение прозрачное шифрование данных на устройство — действие, которое изменяет состояние устройства, в большинстве случаев должен выполняться один раз за время существования устройства и будет выполнена при отсутствии трафика на устройстве.  
  
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
  
  
