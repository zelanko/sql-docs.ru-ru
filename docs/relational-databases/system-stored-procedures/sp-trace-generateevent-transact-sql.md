---
title: sp_trace_generateevent (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_generateevent_TSQL
- sp_trace_generateevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_generateevent
ms.assetid: 3ef05bfb-b467-4403-89cc-6e77ef9247dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: cfeacf9f3c18d3f80b7ad83a3697e33a5797ba22
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68096024"
---
# <a name="sp_trace_generateevent-transact-sql"></a>sp_trace_generateevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает пользовательское событие в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
>**Примечание.**  Эта хранимая процедура **не** является устаревшей. Все остальные хранимые процедуры, связанные с трассировкой, являются устаревшими.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_trace_generateevent [ @eventid = ] event_id   
     [ , [ @userinfo = ] 'user_info' ]  
     [ , [ @userdata = ] user_data ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @eventid = ] event_id`Идентификатор события, которое необходимо включить. *event_id* имеет **тип int**и не имеет значения по умолчанию. Идентификатор должен быть одним из номеров событий от 82 до 91, которые представляют определяемые пользователем события, заданные с помощью [sp_trace_setevent](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
`[ @userinfo = ] 'user_info'`Необязательная определяемая пользователем строка, идентифицирующая причину события. *user_info* имеет тип **nvarchar (128)** и значение по умолчанию NULL.  
  
`[ @userdata = ] user_data`Необязательные определяемые пользователем данные для события. *user_data* имеет тип **varbinary (8000)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В следующей таблице описаны значения кодов, которые могут быть возвращены пользователю при завершении хранимой процедуры.  
  
|Код возврата|Описание|  
|-----------------|-----------------|  
|**0**|Нет ошибки.|  
|**1**|Неизвестная ошибка.|  
|**3**|Указанное событие недопустимо. Возможно, событие не существует или не соответствует ни одной хранимой процедуре.|  
|**13**|Нехватка памяти. Возвращается, когда для выполнения указанного действия недостаточно памяти.|  
  
## <a name="remarks"></a>Remarks  
 **sp_trace_generateevent** выполняет многие действия, ранее выполненные **xp_trace_\* ** расширенными хранимыми процедурами. Вместо **xp_trace_generate_event**используйте **sp_trace_generateevent** .  
  
 С **sp_trace_generateevent**можно использовать только идентификационные номера пользовательских событий. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] активирует ошибку при использовании идентификационных номеров других событий.  
  
 Параметры всех хранимых процедур трассировки SQL (**sp_trace_xx**) строго типизированы. Если эти аргументы указываются с неправильными типами данных входных параметров, как указано в описании их аргументов, хранимая процедура возвратит ошибку.  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен иметь разрешение ALTER TRACE.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается пользовательское событие в образце таблицы.  
  
```  
--Create a sample table.  
CREATE TABLE user_config_test(col1 int, col2 char(10));  
  
--DROP the trigger if it already exists.  
IF EXISTS  
   (SELECT * FROM sysobjects WHERE name = 'userconfig_trg')  
   DROP TRIGGER userconfig_trg;  
  
--Create an ON INSERT trigger on the sample table.  
CREATE TRIGGER userconfig_trg  
   ON user_config_test FOR INSERT;  
AS  
EXEC master..sp_trace_generateevent  
   @event_class = 82, @userinfo = N'Inserted row into user_config_test';  
  
--When an insert action happens, the user-configurable event fires. If   
you were capturing the event id=82, you will see it in the Profiler output.  
INSERT INTO user_config_test VALUES(1, 'abc');  
```  
  
## <a name="see-also"></a>См. также  
 [sys. fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Трассировка SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
