---
title: "sys.fn_trace_getinfo (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs: TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0f7816b4115982fb01f9b456864bb11fc5194ba1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysfntracegetinfo-transact-sql"></a>sys.fn_trace_getinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об указанной трассировке или всех существующих трассировках.  
  
> **ВАЖНО!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.    
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_trace_getinfo ( { trace_id | NULL | 0 | DEFAULT } )  
```  
  
## <a name="arguments"></a>Аргументы  
 *trace_id*  
 Идентификатор трассировки. *trace_id* — **int**.  Допустимыми входными значениями являются идентификатор трассировки, NULL, 0 или DEFAULT. В данном контексте значения NULL, 0 и DEFAULT эквивалентны. Укажите значение NULL, 0 или DEFAULT, чтобы вернуть сведения для всех трассировок в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|traceid|**int**|Идентификатор трассировки.|  
|свойство|**int**|Свойство трассировки:<br /><br /> 1 — параметры трассировки. Дополнительные сведения см. в разделе @options в [sp_trace_create &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).<br /><br /> 2 — имя файла<br /><br /> 3 — максимальный размер<br /><br /> 4 — время остановки<br /><br /> 5 — текущее состояние трассировки. 0 — остановлена. 1 — запущена.|  
|value|**sql_variant**|Сведения о свойстве указанной трассировки.|  
  
## <a name="remarks"></a>Замечания  
 Функция fn_trace_getinfo принимает идентификатор конкретной трассировки и возвращает сведения об этой трассировке. Если передать недопустимый идентификатор, эта функция вернет пустой набор строк.  
  
 Функция fn_trace_getinfo добавляет расширение TRC к имени любого файла трассировки, включенного в ее результирующий набор. Сведения об определении трассировки см. в разделе [sp_trace_create &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md). Аналогичные сведения о фильтрах трассировки см. в разделе [sys.fn_trace_getfilterinfo &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md).  
  
 Полный пример использования хранимых процедур трассировки см. в разделе [создать трассировку &#40; Transact-SQL &#41; ](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER TRACE на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения обо всех активных трассировках.  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [Хранимая процедура sp_trace_generateevent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_geteventinfo &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
