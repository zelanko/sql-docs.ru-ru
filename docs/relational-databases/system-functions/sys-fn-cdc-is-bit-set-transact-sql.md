---
title: sys. fn_cdc_is_bit_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_cdc_is_bit_set
- sys.fn_cdc_is_bit_set_TSQL
- sys.fn_cdc_is_bit_set
- fn_cdc_is_bit_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_is_bit_set
- fn_cdc_is_bit_set
ms.assetid: 792fe7cf-b3b8-4f25-8329-78d63f0e6921
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d14e4e85d6ee52955ba17f42d288e0c770a183a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046352"
---
# <a name="sysfn_cdc_is_bit_set-transact-sql"></a>sys.fn_cdc_is_bit_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает, был ли обновлен отслеживаемый столбец, проверяя установку его порядкового положения в битовой маске.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_is_bit_set ( position , update_mask )  
```  
  
## <a name="arguments"></a>Аргументы  
 *position*  
 Порядковое положение в битовой маске. *позицией* является **int**.  
  
 *update_mask*  
 Маска, идентифицирующая обновленные столбцы. *update_mask* имеет тип **varbinary (128)**.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **bit**  
  
## <a name="remarks"></a>Remarks  
 Эта функция обычно используется как часть запроса изменения данных для определения изменения столбца. В этом сценарии функция [sys. fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md) используется перед запросом для получения необходимого порядкового номера столбца. После этого **sys. fn_cdc_is_bit_set** применяется к каждой строке возвращаемых данных об изменениях, предоставляя сведения о конкретном столбце как часть возвращаемого результирующего набора.  
  
 Мы советуем использовать эту функцию вместо функции [sys. fn_cdc_has_column_changed](../../relational-databases/system-functions/sys-fn-cdc-has-column-changed-transact-sql.md) при определении того, изменились ли столбцы для всех строк возвращенного результирующего набора.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция `sys.fn_cdc_is_bit_set` используется для присоединения к результирующему набору, созданному функцией запроса `cdc.fn_cdc_get_all_changes_HR_Department`, столбца `IsGroupNmUpdated` с помощью предварительно вычисленного порядкового номера столбца и значения `__$update_mask` в качестве аргументов.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10), @GroupNm_ordinal int;  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HR_Department');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SET @GroupNm_ordinal = sys.fn_cdc_get_column_ordinal('HR_Department','GroupName');  
  
SELECT sys.fn_cdc_is_bit_set(@GroupNm_ordinal,__$update_mask) as 'IsGroupNmUpdated', *  
FROM cdc.fn_cdc_get_all_changes_HR_Department( @from_lsn, @to_lsn, 'all')  
WHERE __$operation = 4;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции системы отслеживания измененных данных &#40;языке Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)   
 [sys. fn_cdc_get_column_ordinal &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md)   
 [sys. fn_cdc_has_column_changed &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-has-column-changed-transact-sql.md)   
 [CDC. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [CDC. fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [Об SQL Server &#40;системы отслеживания измененных данных&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
