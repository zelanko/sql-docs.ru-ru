---
title: sp_trace_setfilter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: eeb6fd370bfd107864845439086138fff3d379c2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85644847"
---
# <a name="sp_trace_setfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Применяет фильтр к трассировке. **sp_trace_setfilter** может выполняться только для существующих трассировок, которые остановлены (*Status* имеет значение **0**). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Возвращает ошибку, если эта хранимая процедура выполняется для трассировки, которая не существует или имеет *состояние* , не равное **0**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
  
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
`[ @traceid = ] trace_id`Идентификатор трассировки, для которой задан фильтр. *trace_id* имеет **тип int**и не имеет значения по умолчанию. Пользователь использует это *trace_id* значение для выявления, изменения и управления трассировкой.  
  
`[ @columnid = ] column_id`Идентификатор столбца, к которому применяется фильтр. *column_id* имеет **тип int**и не имеет значения по умолчанию. Если *column_id* имеет значение null, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очищает все фильтры для указанной трассировки.  
  
`[ @logical_operator = ] logical_operator`Указывает, применяется ли оператор AND (**0**) или OR (**1**). *logical_operator* имеет **тип int**и не имеет значения по умолчанию.  
  
`[ @comparison_operator = ] comparison_operator`Указывает тип выполняемого сравнения. *comparison_operator* имеет **тип int**и не имеет значения по умолчанию. В таблице содержатся операторы сравнения и представляющие их значения.  
  
|Применение|Оператор сравнения|  
|-----------|-------------------------|  
|**0**|= (равно)|  
|**1**|<>  (не равно)|  
|**2**|> (больше)|  
|**3**|< (Меньше)|  
|**4**|>= (больше или равно)|  
|**5**|<= (меньше или равно)|  
|**6**|LIKE|  
|**7**|Не похоже|  
  
`[ @value = ] value`Задает значение для фильтрации. Тип данных *значения* должен соответствовать типу данных фильтруемого столбца. Например, если фильтр установлен для столбца идентификатора объекта, который является типом данных **int** , то *значение* должно быть **int**. Если *значение value* равно **nvarchar** или **varbinary**, оно может иметь максимальную длину 8000.  
  
 Когда оператором сравнения является LIKE или NOT LIKE, то логический оператор может содержать «%» или другой фильтр, подходящий для операции LIKE.  
  
 Можно указать *значение* null, чтобы отфильтровать события со значениями СТОЛБЦОВ, равными null. Только операторы **0** (= EQUAL) и **1** (<> не равно) являются допустимыми со значением NULL. В таком случае эти операторы эквивалентны операторам [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL и IS NOT NULL.  
  
 Чтобы применить фильтр между диапазонами значений столбцов, **sp_trace_setfilter** должен выполняться дважды — один раз с оператором сравнения "больше или равно" (">=") и еще один раз с оператором "меньше или равно" (' <= ').  
  
 Дополнительные сведения о типах данных столбцов данных см. в [справочнике по классам событий SQL Server](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В следующей таблице описаны значения кодов, которые могут быть возвращены пользователю при завершении хранимой процедуры.  
  
|Код возврата|Описание|  
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
  
## <a name="remarks"></a>Примечания  
 **sp_trace_setfilter** — это [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимая процедура, которая выполняет многие действия, ранее выполненные расширенными хранимыми процедурами, доступными в более ранних версиях служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Используйте **sp_trace_setfilter** вместо **xp_trace_set \* фильтрации** расширенных хранимых процедур для создания, применения и удаления фильтров в трассировке. Дополнительные сведения см. [в разделе Фильтрация трассировки](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 Все фильтры для определенного столбца должны быть включены одновременно в одном выполнении **sp_trace_setfilter**. Например, если пользователь собирается применить два фильтра к столбцу имен приложений и один фильтр к столбцу имен пользователей, то ему потребуется указать фильтры для имен приложений последовательно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает ошибку, когда пользователь пытается указать фильтр по имени приложения в пределах одного хранимого вызова процедуры, за которым указывается фильтр по имени пользователя, после чего — второй фильтр по имени приложения.  
  
 Параметры всех хранимых процедур трассировки SQL (**sp_trace_xx**) строго типизированы. Если эти параметры не вызываются вместе с правильными типами данных входных параметров, как указано в описании аргумента, хранимая процедура возвращает ошибку.  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен иметь разрешение ALTER TRACE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере устанавливается три фильтра на трассировку `1`. Фильтры `N'SQLT%'` и `N'MS%'` устанавливаются на один столбец (`AppName`, значение `10`) с помощью оператора сравнения `LIKE`. Фильтр `N'joe'` устанавливается на другой столбец (`UserName`, значение `11`) с помощью оператора сравнения `EQUAL`.  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>См. также  
 [sys. fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys. fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Трассировка SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
