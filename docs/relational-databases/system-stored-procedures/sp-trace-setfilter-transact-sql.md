---
title: "sp_trace_setfilter (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 01394d92e71c69de60bbf2015ea58c4c8d53f0a4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sptracesetfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Применяет фильтр к трассировке. **sp_trace_setfilter** может выполняться только для существующих остановленных трассировок (*состояние* — **0**). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Возвращает сообщение об ошибке, если эта хранимая процедура выполняется для трассировки, которая не существует или которого *состояние* не **0**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@traceid=** ] *trace_id*  
 Идентификатор трассировки, для которой устанавливается фильтр. *trace_id* — **int**, не имеет значения по умолчанию. Пользователь применяет это *trace_id* значение для определения, изменения и управления трассировкой.  
  
 [  **@columnid=** ] *column_id*  
 Является идентификатором столбца, к которому применяется фильтр. *Идентификатор column_id* — **int**, не имеет значения по умолчанию. Если *column_id* имеет значение NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет все фильтры для указанной трассировки.  
  
 [  **@logical_operator**  =] *logical_operator*  
 Указывает, является ли AND (**0**) или OR (**1**) применяется оператор. *logical_operator* — **int**, не имеет значения по умолчанию.  
  
 [  **@comparison_operator=** ] *оператор_сравнения*  
 Задает тип сравнения, которое будет выполнено. *оператор_сравнения* — **int**, не имеет значения по умолчанию. В таблице содержатся операторы сравнения и представляющие их значения.  
  
|Значение|Оператор сравнения|  
|-----------|-------------------------|  
|**0**|= (равно)|  
|**1**|<> (не равно)|  
|**2**|> (больше)|  
|**3**|< (меньше)|  
|**4**|>= (больше или равно)|  
|**5**|<= (меньше или равно)|  
|**6**|LIKE|  
|**7**|Не похоже|  
  
 [  **@value=** ] *значение*  
 Определяет значение, с помощью которого будет выполняться фильтрация. Тип данных *значение* должен соответствовать типу данных столбца для фильтрации. Например, если фильтр применен к столбцу Object ID, **int** тип данных *значение* должно быть **int**. Если *значение* — **nvarchar** или **varbinary**, он может иметь длину не больше 8000.  
  
 Когда оператором сравнения является LIKE или NOT LIKE, то логический оператор может содержать «%» или другой фильтр, подходящий для операции LIKE.  
  
 Можно указать значение NULL для *значение* чтобы отфильтровать события со значениями столбцов NULL. Только **0** (= равно) и **1** операторы (<> не равно) могут иметь значение NULL. В таком случае эти операторы эквивалентны операторам [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL и IS NOT NULL.  
  
 Чтобы применить фильтр из диапазона значений столбцов **sp_trace_setfilter** необходимо выполнить дважды — один раз с большей больше или равно ("> =") оператор сравнения, а второй раз с менее больше или равно ("< =") оператор .  
  
 Дополнительные сведения о типах данных столбцов см. в разделе [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В следующей таблице описаны значения кодов, которые могут быть возвращены пользователю при завершении хранимой процедуры.  
  
|Код возврата|Description|  
|-----------------|-----------------|  
|0|Нет ошибки.|  
|1|Неизвестная ошибка.|  
|2|Трассировка в данный момент выполняется. Изменение трассировки в это время приведет к ошибке.|  
|4|Указан недопустимый столбец.|  
|5|Нельзя выполнить фильтрацию по указанному столбцу. Это значение возвращается только из **sp_trace_setfilter**.|  
|6|Указан недопустимый оператор сравнения.|  
|7|Указан недопустимый логический оператор.|  
|9|Указан недопустимый дескриптор трассировки.|  
|13|Нехватка памяти. Возвращается, когда для выполнения указанного действия недостаточно памяти.|  
|16|Недопустимая функция для данной трассировки.|  
  
## <a name="remarks"></a>Замечания  
 **sp_trace_setfilter** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимую процедуру, которая выполняет многие действия, ранее выполнявшиеся расширенными хранимыми процедурами в более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте **sp_trace_setfilter** вместо **xp_trace_set\*фильтра** расширенные хранимые процедуры для создания, применения, удаления или управлять фильтров в трассировках. Дополнительные сведения см. в разделе [фильтра трассировки](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 Все фильтры для определенного столбца должны быть одновременно разрешены однократным выполнением **sp_trace_setfilter**. Например, если пользователь собирается применить два фильтра к столбцу имен приложений и один фильтр к столбцу имен пользователей, то ему потребуется указать фильтры для имен приложений последовательно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку, когда пользователь пытается указать фильтр по имени приложения в пределах одного хранимого вызова процедуры, за которым указывается фильтр по имени пользователя, после чего — второй фильтр по имени приложения.  
  
 Параметры всех трассировки SQL хранимые процедуры (**sp_trace_xx**) жестко типизированы. Если эти параметры не вызываются вместе с правильными типами данных входных параметров, как указано в описании аргумента, хранимая процедура возвращает ошибку.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен иметь разрешение ALTER TRACE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере устанавливается три фильтра на трассировку `1`. Фильтры `N'SQLT%'` и `N'MS%'` устанавливаются на один столбец (`AppName`, значение `10`) с помощью оператора сравнения `LIKE`. Фильтр `N'joe'` устанавливается на другой столбец (`UserName`, значение `11`) с помощью оператора сравнения `EQUAL`.  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fn_trace_getfilterinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Трассировка SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
