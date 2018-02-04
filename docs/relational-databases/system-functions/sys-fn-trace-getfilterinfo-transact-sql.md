---
title: "sys.fn_trace_getfilterinfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_trace_getfilterinfo
- fn_trace_getfilterinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], filters
- sys.fn_trace_getfilterinfo function
- filters [SQL Server], traces
- fn_trace_getfilterinfo function
ms.assetid: 09fe4a28-ff8a-4655-9da1-4654d5bc514d
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e29c80f8a8c0999e1c635c7271c48f4d87697283
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysfntracegetfilterinfo-transact-sql"></a>sys.fn_trace_getfilterinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о фильтрах, примененных к указанной трассировке.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_trace_getfilterinfo ( trace_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *trace_id*  
 Идентификатор трассировки. *trace_id* — **int**, не имеет значения по умолчанию.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Возвращает следующие данные. Дополнительные сведения о столбцах см. в разделе [sp_trace_setfilter &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**columnid**|**int**|Идентификатор столбца, к которому применяется фильтр.|  
|**logical_operator**|**int**|Указывает, какой применяется оператор: AND или OR.|  
|**comparison_operator**|**int**|Задает тип сравнения.<br /><br /> 0 = равны.<br /><br /> 1 = не равны.<br /><br /> 2 = больше чем.<br /><br /> 3 = меньше чем.<br /><br /> 4 = больше или равно.<br /><br /> 5 = меньше или равно.<br /><br /> 6 = схожи.<br /><br /> 7 = не схожи.|  
|**value**|**sql_variant**|Задает значение, к которому применяется фильтр.|  
  
## <a name="remarks"></a>Remarks  
 Наборы пользователей *trace_id* значение для определения, изменения и управления трассировкой. Идентификатор конкретной трассировки **fn_trace_getfilterinfo** возвращает сведения о любой фильтр к данной трассировке. Если к указанной трассировке не применяются фильтры, функция возвращает пустой набор строк. Если передать недопустимый идентификатор, эта функция вернет пустой набор строк. Аналогичные сведения о трассировках см. в разделе [sys.fn_trace_getinfo &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER TRACE на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения обо всех фильтрах, применяемых к трассировке 2.  
  
```  
SELECT * FROM fn_trace_getfilterinfo(2) ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
