---
title: "Инструкция WAITFOR (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WAITFOR
- WAITFOR_TSQL
dev_langs: TSQL
helpviewer_keywords:
- TIME option
- delaying executions [SQL Server]
- batches [SQL Server], execution times
- stored procedures [SQL Server], executing
- DELAY
- time [SQL Server], execution delays
- blocking executions
- transactions [SQL Server], execution times
- WAITFOR statement
- timing executions
ms.assetid: 8e896e73-af27-4cae-a725-7a156733f3bd
caps.latest.revision: "40"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2a1453c5d7beaf9d4ab9d140a0414e730c9d651a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="waitfor-transact-sql"></a>WAITFOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Блокирует выполнение пакета, хранимой процедуры или транзакции до наступления указанного времени или интервала времени, либо заданная инструкция изменяет или возвращает, по крайней мере, одну строку.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WAITFOR   
{  
    DELAY 'time_to_pass'   
  | TIME 'time_to_execute'   
  | [ ( receive_statement ) | ( get_conversation_group_statement ) ]   
    [ , TIMEOUT timeout ]  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 DELAY  
 Заданный период времени (не более 24 часов), который должен пройти до выполнения пакета, хранимой процедуры или продолжения транзакции.  
  
 '*time_to_pass*'  
 Период времени ожидания. *time_to_pass* может быть указан в одном из допустимых форматов для **datetime** данных или его можно указать как локальная переменная. Невозможно указать даты; Таким образом, часть даты **datetime** значение недопустимо.  
  
 TIME  
 Заданное время выполнения пакета, хранимой процедуры или транзакции.  
  
 '*time_to_execute*'  
 Время, в которое инструкция WAITFOR завершает работу. *time_to_execute* может быть указан в одном из допустимых форматов для **datetime** данных или его можно указать как локальная переменная. Невозможно указать даты; Таким образом, часть даты **datetime** значение недопустимо.  
  
 *receive_statement*  
 Допустимая инструкция RECEIVE.  
  
> [!IMPORTANT]  
>  Инструкция WAITFOR с *receive_statement* применимо только к [!INCLUDE[ssSB](../../includes/sssb-md.md)] сообщений. Дополнительные сведения см. в разделе [RECEIVE &#40; Transact-SQL &#41; ](../../t-sql/statements/receive-transact-sql.md).  
  
 *get_conversation_group_statement*  
 Допустимая инструкция GET CONVERSATION GROUP.  
  
> [!IMPORTANT]  
>  Инструкция WAITFOR с *get_conversation_group_statement* применимо только к [!INCLUDE[ssSB](../../includes/sssb-md.md)] сообщений. Дополнительные сведения см. в разделе [GET CONVERSATION GROUP &#40; Transact-SQL &#41; ](../../t-sql/statements/get-conversation-group-transact-sql.md).  
  
 Время ОЖИДАНИЯ *время ожидания*  
 Указывает период времени ожидания очередного сообщения (в миллисекундах).  
  
> [!IMPORTANT]  
>  Инструкция WAITFOR с аргументом TIMEOUT применима только к сообщениям компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Дополнительные сведения см. в разделе [RECEIVE &#40; Transact-SQL &#41; ](../../t-sql/statements/receive-transact-sql.md) и [GET CONVERSATION GROUP &#40; Transact-SQL &#41; ](../../t-sql/statements/get-conversation-group-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Во время выполнения инструкции WAITFOR выполняется транзакция, и другие запросы не могут быть выполнены в рамках этой транзакции.  
  
 Действительная продолжительность задержки может отличаться от времени, указанного в *time_to_pass*, *time_to_execute*, или *время ожидания* и зависит от уровня активности сервера. Счетчик времени запускается, когда запланирован поток, связанный с инструкцией WAITFOR. Если сервер занят, запланированный запуск потока может оказаться невозможным, поэтому время задержки может оказаться больше заданного.  
  
 Инструкция WAITFOR не изменяет семантику запроса. Если запрос не может возвратить строки, инструкция WAITFOR будет ждать неограниченное время или до достижения TIMEOUT, если он был задан.  
  
 Для инструкций WAITFOR невозможно открыть курсоры.  
  
 Для инструкций WAITFOR невозможно указать представления.  
  
 Если запрос превышает значение, заданное аргументом query  wait, параметр инструкции WAITFOR может завершиться без выполнения. Дополнительные сведения об этом параметре конфигурации см. в разделе [Настройка параметра конфигурации сервера query wait](../../database-engine/configure-windows/configure-the-query-wait-server-configuration-option.md). Чтобы просмотреть активные и ожидающие процессы, используйте [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md).  
  
 Каждая инструкция WAITFOR имеет связанный с ней поток. Если на одном сервере задано несколько инструкций WAITFOR, то можно объединить несколько потоков, ожидающих выполнения этих инструкций. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отслеживает количество потоков, связанных с инструкциями WAITFOR, и случайным образом завершает работу нескольких из этих потоков, если на сервере имеет место нехватка потоков.  
  
 Можно создать взаимоблокировку, выполнив запрос с инструкцией WAITFOR в транзакции, также поддерживающей блокировки для предотвращения изменений набора строк, к которым пытается обратиться инструкция WAITFOR. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицирует эти сценарии и возвращает пустой результирующий набор, если есть вероятность такой взаимоблокировки.  
  
> [!CAUTION]  
>  Использование указания WAITFOR приведет к замедлению выполнения процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в результате чего в приложении может открыться сообщение об истечении времени ожидания. При необходимости отрегулируйте значение времени ожидания для соединения на уровне приложения.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-waitfor-time"></a>A. Использование инструкции WAITFOR TIME  
 В следующем примере выполняется хранимая процедура `sp_update_job` в базе данных msdb в 22:20. (`22:20`).  
  
```  
EXECUTE sp_add_job @job_name = 'TestJob';  
BEGIN  
    WAITFOR TIME '22:20';  
    EXECUTE sp_update_job @job_name = 'TestJob',  
        @new_name = 'UpdatedJob';  
END;  
GO  
```  
  
### <a name="b-using-waitfor-delay"></a>Б. Использование WAITFOR DELAY  
 В следующем примере хранимая процедура выполняется после 2-часовой задержки.  
  
```  
BEGIN  
    WAITFOR DELAY '02:00';  
    EXECUTE sp_helpdb;  
END;  
GO  
```  
  
### <a name="c-using-waitfor-delay-with-a-local-variable"></a>В. Использование WAITFOR DELAY с локальной переменной  
 Следующий пример показывает, как можно использовать локальную переменную с параметром `WAITFOR DELAY`. Хранимая процедура создается для ожидания переменного периода времени и возвращает пользователю данные относительно количества истекших часов, минут и секунд.  
  
```  
IF OBJECT_ID('dbo.TimeDelay_hh_mm_ss','P') IS NOT NULL  
    DROP PROCEDURE dbo.TimeDelay_hh_mm_ss;  
GO  
CREATE PROCEDURE dbo.TimeDelay_hh_mm_ss   
    (  
    @DelayLength char(8)= '00:00:00'  
    )  
AS  
DECLARE @ReturnInfo varchar(255)  
IF ISDATE('2000-01-01 ' + @DelayLength + '.000') = 0  
    BEGIN  
        SELECT @ReturnInfo = 'Invalid time ' + @DelayLength   
        + ',hh:mm:ss, submitted.';  
        -- This PRINT statement is for testing, not use in production.  
        PRINT @ReturnInfo   
        RETURN(1)  
    END  
BEGIN  
    WAITFOR DELAY @DelayLength  
    SELECT @ReturnInfo = 'A total time of ' + @DelayLength + ',   
        hh:mm:ss, has elapsed! Your time is up.'  
    -- This PRINT statement is for testing, not use in production.  
    PRINT @ReturnInfo;  
END;  
GO  
/* This statement executes the dbo.TimeDelay_hh_mm_ss procedure. */  
EXEC TimeDelay_hh_mm_ss '00:00:10';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `A total time of 00:00:10, in hh:mm:ss, has elapsed. Your time is up.`  
  
## <a name="see-also"></a>См. также  
 [Язык управления выполнением &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [DateTime &#40; Transact-SQL &#41;](../../t-sql/data-types/datetime-transact-sql.md)   
 [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
