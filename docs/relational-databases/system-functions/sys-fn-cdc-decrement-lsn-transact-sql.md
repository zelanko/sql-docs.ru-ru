---
title: sys. fn_cdc_decrement_lsn (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_cdc_decrement_lsn
- sys.fn_cdc_decrement_lsn_TSQL
- sys.fn_cdc_decrement_lsn
- fn_cdc_decrement_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_decrement_lsn
- sys.fn_cdc_decrement_lsn
ms.assetid: 83c182ad-4713-439b-8769-9b7408aec8b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 468fa452a5b9015bf5fcc613c040f76160e87210
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046515"
---
# <a name="sysfn_cdc_decrement_lsn-transact-sql"></a>sys.fn_cdc_decrement_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает предыдущий регистрационный номер транзакции в журнале (LSN) в последовательности, основанной на заданном номере LSN.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_cdc_decrement_lsn ( lsn_value )  
```  
  
## <a name="arguments"></a>Аргументы  
 *lsn_value*  
 Значение LSN. *lsn_value* является **двоичным (10)**.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **двоичный (10)**  
  
## <a name="remarks"></a>Remarks  
 Номер LSN, возвращаемый этой функцией, всегда меньше указанного значения, и между этими двумя значениями не могут существовать другие номера LSN.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных **Public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция `sys.fn_cdc_decrement_lsn` используется для установки верхней границы номеров LSN в запросе, возвращающем строки информации об изменениях, имеющих номера LSN меньше максимального значения LSN.  
  
```  
Use AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_decrement_lsn(sys.fn_cdc_get_max_lsn());  
SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee( @from_lsn, @to_lsn, 'all');   
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys. fn_cdc_increment_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)   
 [sys. fn_cdc_get_min_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys. fn_cdc_get_max_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-max-lsn-transact-sql.md)   
 [&#40;SQL Server журнала транзакций&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [Об SQL Server &#40;системы отслеживания измененных данных&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
