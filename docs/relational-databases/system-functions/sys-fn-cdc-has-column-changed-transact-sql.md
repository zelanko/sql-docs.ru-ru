---
title: sys. fn_cdc_has_column_changed (Transact-SQL) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046378"
---
# <a name="sysfn_cdc_has_column_changed-transact-sql"></a>sys.fn_cdc_has_column_changed (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет, указывает ли заданная маска обновления на обновление заданного столбца в связанной строке изменений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_has_column_changed ( 'capture_instance','column_name' , update_mask )  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *capture_instance* **"**  
 Имя экземпляра отслеживания. *capture_instance* имеет тип **sysname**.  
  
 **"** *column_name* **"**  
 Отслеживаемый столбец заданного экземпляра отслеживания. *column_name* имеет тип **sysname**.  
  
 *update_mask*  
 Маска, идентифицирующая обновленные столбцы во всех связанных строках изменения. *update_mask* имеет тип **varbinary (128)**.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **bit**  
  
## <a name="remarks"></a>Remarks  
 Эту функцию можно использовать для получения сведений из маски обновления, которая возвращается в запросе данных изменений. Она особенно полезна во время последующей обработки маски обновления, когда нужно определить, изменился ли конкретный столбец в связанной строке изменений. Дополнительные сведения см. в статье [О системе отслеживания измененных данных (SQL Server)](../../relational-databases/track-changes/about-change-data-capture-sql-server.md).  
  
 Если эта информация будет возвращена как часть запроса на изменение данных, вместо этой функции рекомендуется использовать функции [sys. fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md) и [sys. fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) . Используйте функцию fn_cdc_get_column_ordinal перед запросом на изменение данных, чтобы нужный порядковый номер столбца вычисляться только один раз. Используйте fn_cdc_is_bit_set в запросе, чтобы извлечь сведения из маски обновления для каждой возвращаемой строки.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера sysadmin или предопределенной роли базы данных db_owner. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных.  
  
## <a name="see-also"></a>См. также:  
 [CDC. &#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)   
 [CDC. captured_columns &#40;&#41;Transact-SQL](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
  
  
