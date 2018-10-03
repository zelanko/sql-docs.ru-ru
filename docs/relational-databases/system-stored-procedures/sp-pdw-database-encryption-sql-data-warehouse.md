---
title: sp_pdw_database_encryption (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: eeb1263c02b9b06ffe747b78f8dae5691b7f92fd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846622"
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
 [  **@enabled=** ] *включена*  
 Определяет, включено ли прозрачное шифрование данных. *включить* — **int**, и может принимать одно из следующих значений:  
  
-   0 = Отключено  
  
-   1 = Включено  
  
 Выполнение **sp_pdw_database_encryption** без параметров возвращает текущее состояние прозрачного шифрования данных на устройстве как набор скалярный результат: 0 для отключено или 1 для включена.  
  
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
  
  
