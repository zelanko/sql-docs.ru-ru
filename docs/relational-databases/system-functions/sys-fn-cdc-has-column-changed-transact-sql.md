---
title: sys.fn_cdc_has_column_changed (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_has_column_changed_TSQL
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed_TSQL
- fn_cdc_has_column_changed
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed
ms.assetid: 2b9e6278-050d-4ffc-8d1a-09606180facc
author: rothja
ms.author: jroth
ms.openlocfilehash: 9c409581771055e2c6d85d2cdd01937e2f033ba9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68046378"
---
# <a name="sysfncdchascolumnchanged-transact-sql"></a>sys.fn_cdc_has_column_changed (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет, указывает ли заданная маска обновления на обновление заданного столбца в связанной строке изменений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_has_column_changed ( 'capture_instance','column_name' , update_mask )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *capture_instance* **"**  
 Имя экземпляра отслеживания. *capture_instance* — **sysname**.  
  
 **"** *column_name* **"**  
 Отслеживаемый столбец заданного экземпляра отслеживания. *column_name* — **sysname**.  
  
 *update_mask*  
 Маска, идентифицирующая обновленные столбцы во всех связанных строках изменения. *update_mask* — **varbinary(128)** .  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **bit**  
  
## <a name="remarks"></a>Примечания  
 Эту функцию можно использовать для получения сведений из маски обновления, которая возвращается в запросе данных изменений. Она особенно полезна во время последующей обработки маски обновления, когда нужно определить, изменился ли конкретный столбец в связанной строке изменений. Дополнительные сведения см. в статье [О системе отслеживания измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md).  
  
 Если эти сведения возвращаются как часть запроса измененных данных, мы рекомендуем использовать функции [sys.fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md) и [sys.fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) вместо этой функции. Используйте функцию fn_cdc_get_column_ordinal перед выполнением запроса информации об изменениях, таким образом, чтобы номер нужного столбца вычислялся вычисляется только один раз. Используйте fn_cdc_is_bit_set в запросе для извлечения сведений из маски обновления для каждой строки.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных.  
  
## <a name="see-also"></a>См. также  
 [CDC. &#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)   
 [CDC.captured_columns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
  
  
