---
title: sys.fn_trace_getinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_trace_getinfo
- fn_trace_getinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- traces [SQL Server], status information
- status information [SQL Server], traces
- sys.fn_trace_getinfo function
- fn_trace_getinfo function
ms.assetid: 04b140fe-110a-47b8-98b5-e4c161beb6c9
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f709ba43a3dda3b219c083449869a6963da003f5
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38056198"
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
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|traceid|**int**|Идентификатор трассировки.|  
|свойство|**int**|Свойство трассировки:<br /><br /> 1 — параметры трассировки. Дополнительные сведения см. в разделе @options в [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md).<br /><br /> 2 — имя файла<br /><br /> 3 — максимальный размер<br /><br /> 4 — время остановки<br /><br /> 5 — текущее состояние трассировки. 0 — остановлена. 1 — запущена.|  
|value|**sql_variant**|Сведения о свойстве указанной трассировки.|  
  
## <a name="remarks"></a>Примечания  
 Функция fn_trace_getinfo принимает идентификатор конкретной трассировки и возвращает сведения об этой трассировке. Если передать недопустимый идентификатор, эта функция вернет пустой набор строк.  
  
 Функция fn_trace_getinfo добавляет расширение TRC к имени любого файла трассировки, включенного в ее результирующий набор. Дополнительные сведения об определении трассировки см. в разделе [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md). Аналогичные сведения о фильтрах трассировки см. в разделе [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md).  
  
 Полный пример использования хранимых процедур трассировки см. в разделе [создать трассировку &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER TRACE на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения обо всех активных трассировках.  
  
```  
SELECT * FROM sys.fn_trace_getinfo(0) ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [Хранимая процедура sp_trace_create (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [Хранимая процедура sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_getfilterinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
