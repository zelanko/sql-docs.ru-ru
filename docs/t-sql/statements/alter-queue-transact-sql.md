---
title: "ALTER QUEUE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_QUEUE_TSQL
- ALTER QUEUE
dev_langs: TSQL
helpviewer_keywords:
- number of queue readers
- modifying queues
- ALTER QUEUE statement
- queue readers [SQL Server]
- queues [Service Broker], modifying
- unavailable queues [SQL Server]
- activation stored procedures [Service Broker]
ms.assetid: d54aa325-8761-4cd4-8da7-acf33df12296
caps.latest.revision: "49"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f97bd0a341ecc5e960c94c4c8bdabe30b572fd9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="alter-queue-transact-sql"></a>ALTER QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства очереди.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER QUEUE <object>   
   queue_settings  
   | queue_action  
[ ; ]  
  
<object> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        queue_name  
}   
  
<queue_settings> : :=  
WITH  
   [ STATUS = { ON | OFF } [ , ] ]  
   [ RETENTION = { ON | OFF } [ , ] ]  
   [ ACTIVATION (  
       { [ STATUS = { ON | OFF } [ , ] ]   
         [ PROCEDURE_NAME = <procedure> [ , ] ]  
         [ MAX_QUEUE_READERS = max_readers [ , ] ]  
         [ EXECUTE AS { SELF | 'user_name'  | OWNER } ]  
       |  DROP }  
          ) [ , ]]  
         [ POISON_MESSAGE_HANDLING (  
          STATUS = { ON | OFF } )  
         ]   
  
<queue_action> : :=  
   REBUILD [ WITH <query_rebuild_options> ]  
   | REORGANIZE [ WITH (LOB_COMPACTION = { ON | OFF } ) ]  
   | MOVE TO { file_group | "default" }  
  
<procedure> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        stored_procedure_name  
}  
  
<queue_rebuild_options> : :=  
{  
   ( MAXDOP = max_degree_of_parallelism )  
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* (object)  
 Название базы данных, которая содержит изменяемую очередь. Если аргумент *имя_базы_данных* указан, по умолчанию используется текущая база данных.  
  
 *schema_name* (object)  
 Имя схемы, которой принадлежит новая очередь. Если аргумент *schema_name* указан, по умолчанию используется схема по умолчанию для текущего пользователя.  
  
 *queue_name*  
 Имя изменяемой очереди.  
  
 STATUS (очередь)  
 Указывает, доступна очередь (ON) или нет (OFF). Когда очередь недоступна, нельзя ни добавлять в нее сообщения, ни удалять их из нее.  
  
 RETENTION  
 Указывает параметр хранения для очереди. Если указано RETENTION = ON, все сообщения, посылаемые или отправляемые во время диалогов, которые используют данную очередь, хранятся в очереди до окончания этих диалогов. Это позволяет сохранять сообщения для целей ревизии или для выполнения компенсирующих транзакций, если возникают ошибки  
  
> [!NOTE]  
>  Установка RETENTION = ON может уменьшить производительность. Эта установка должна использоваться только тогда, когда необходимо достичь соглашения уровня службы для приложения.  
  
 ACTIVATION  
 Указывает сведения о хранимой процедуре, которая активизируется для обработки сообщений, которые поступают в данную очередь.  
  
 STATUS (активация)  
 Указывает, активирует ли очередь хранимую процедуру. Если параметр STATUS = ON, то очередь запускает хранимую процедуру, указанную параметром PROCEDURE_NAME, если количество выполняемых в настоящий момент хранимых процедур меньше, чем значение MAX_QUEUE_READERS, и если сообщения прибывают в очередь быстрее, чем хранимые процедуры получают сообщения. Если параметр STATUS = OFF, очередь не активирует хранимую процедуру.  
  
 ПЕРЕСТРОИТЬ [WITH \<queue_rebuild_options >]  
 **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Перестраиваются все индексы внутренней таблицы очереди. Эту возможность следует используйте, если вы испытываете проблемы с фрагментацией из-за высокой нагрузки. MAXDOP — единственный поддерживаемый очереди параметр rebuild. ПЕРЕСТРОЕНИЕ всегда является операцией вне сети.  
  
 РЕОРГАНИЗАЦИЯ [С (LOB_COMPACTION = {ON | OFF})]  
 **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Реорганизация всех индексов в таблице внутренней очереди.   
В отличие от REORGANIZE пользовательской таблицы REORGANIZE в очереди всегда выполняется как операцию в автономном режиме из-за блокировки на уровне страницы явно отключено в очереди.  
  
> [!TIP]  
>  Общие рекомендации по фрагментации индекса Если фрагментация находится между 5% до 30%, реорганизации индекса. Если фрагментация больше 30%, необходимо перестройте индекс. Однако эти числа предназначены только для общих рекомендаций в качестве отправной точки для вашей среды. Чтобы определить степень фрагментации индекса, используйте [sys.dm_db_index_physical_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) -см. пример Ж в этой статье примеры.  
  
 ПЕРЕМЕСТИТЬ в { *file_group* | «default»}  
 **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Перемещает внутренней таблицы очереди (с его индексов) пользователя в указанной файловой группе.  Новая файловая группа не должен быть доступен только для чтения.  
  
 Procedure_name = \<процедуры >  
 Указывает имя активируемой хранимой процедуры, если очередь содержит сообщения, которые нужно обработать. Это значение должно являться идентификатором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *database_name* (процедура)  
 Имя базы данных, которая содержит хранимую процедуру.  
  
 *schema_name* (процедура)  
 Имя схемы, которой принадлежит хранимая процедура.  
  
 *stored_procedure_name*  
 Имя хранимой процедуры.  
  
 MAX_QUEUE_READERS =*max_reader*  
 Указывает максимальное число экземпляров хранимой процедуры активации, которые очередь одновременно может запустить. Значение *аргумента max_readers* должно быть числом от 0 до 32767.  
  
 EXECUTE AS  
 Указывает учетную запись пользователя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], от имени которого выполняется хранимая процедура активации. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность проверить разрешения для этого пользователя в момент, когда очередь активирует хранимую процедуру. Для пользователя домена Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть подключен к домену и иметь возможность проверить разрешения указанного пользователя при активизации процедуры или неудачной попытке запуска процедуры. Для пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сервер всегда в состоянии проверить разрешения.  
  
 SELF  
 Указывает, что хранимая процедура выполняется как текущий пользователь. (Участник базы данных, выполняющий эту инструкцию ALTER QUEUE)  
  
 '*user_name*'  
 Имя пользователя, от имени которого выполняется хранимая процедура. *имя_пользователя* должен быть допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователя, указанного как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификатор. Текущий пользователь должен иметь разрешение IMPERSONATE для *имя_пользователя* указанного.  
  
 OWNER  
 Указывает, что хранимая процедура выполняется в контексте владельца очереди.  
  
 DROP  
 Удаляет все сведения об активации, ассоциированные с очередью.  
  
 POISON_MESSAGE_HANDLING  
 Указывает, включена ли обработка сообщений о сбое. Значение по умолчанию — ON.  
  
 Очередь, в которой параметру обработки сообщений о сбое задано значение OFF, не будет отключена после пяти последовательных откатов транзакций. Это позволяет приложению определить пользовательскую систему обработки опасных сообщений.  
  
## <a name="remarks"></a>Remarks  
 Если очередь с указанной хранимой процедурой активации содержит сообщения, которые изменяют состояние активации с OFF на ON, тут же активирует хранимую процедуру активации. Изменение состояния активации с ON на OFF прекращает активацию экземпляров хранимой процедуры брокером, но не останавливает экземпляры хранимой процедуры, которые уже запущены.  
  
 Изменение очереди для добавления хранимой процедуры активации не изменяет состояния активации очереди. Изменение хранимой процедуры активации для очереди не влияет на экземпляры хранимых процедур активации, которые уже запущены.  
  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] проверяет максимальное число агентов чтения очереди для очереди в качестве части процесса активации. Поэтому, изменение очереди с целью увеличения максимального числа агентов чтения очереди позволяет компоненту [!INCLUDE[ssSB](../../includes/sssb-md.md)] немедленно запустить больше экземпляров хранимой процедуры активации. Изменение очереди с целью уменьшения максимального числа агентов чтения очереди не влияет на экземпляры хранимой процедуры активации, которые уже запущены. Однако компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] не запускает новый экземпляр хранимой процедуры до тех пор, пока число экземпляров хранимой процедуры активации не уменьшится до заданного максимального числа.  
  
 Если очередь недоступна, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] сохраняет сообщения для служб, пользующихся данной очередью, в очереди передачи для базы данных. [Sys.transmission_queue](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md) представление каталога содержит представление очереди передачи.  
  
 Если инструкция RECEIVE или инструкция GET CONVERSATION GROUP указывает недоступную очередь, выполнение инструкции завершается ошибкой языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешением на изменения значений очереди обладает владелец типа сообщений, члены предопределенной роли базы данных db_ddladmin или db_owner и члены предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-making-a-queue-unavailable"></a>A. Как сделать очередь недоступной  
 В этом примере очередь `ExpenseQueue` делается недоступной для приема сообщений.  
  
```  
ALTER QUEUE ExpenseQueue WITH STATUS = OFF ;  
```  
  
### <a name="b-changing-the-activation-stored-procedure"></a>Б. Изменение хранимой процедуры активации  
 Следующий пример изменяет хранимую процедуру, которую запускает очередь. Хранимая процедура выполняется в контексте пользователя, выполнившего инструкцию `ALTER QUEUE`.  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = new_stored_proc,  
        EXECUTE AS SELF) ;  
```  
  
### <a name="c-changing-the-number-of-queue-readers"></a>В. Изменение числа агентов чтения очереди  
 Следующий пример устанавливает максимальное число экземпляров хранимых процедур, запускаемых компонентом [!INCLUDE[ssSB](../../includes/sssb-md.md)] для этой очереди, равное `7`.  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (MAX_QUEUE_READERS = 7) ;  
```  
  
### <a name="d-changing-the-activation-stored-procedure-and-the-execute-as-account"></a>Г. Изменение хранимой процедуры активации и учетной записи EXECUTE AS  
 Следующий пример изменяет хранимую процедуру, которую запускает компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Хранимая процедура выполняется в контексте пользователя `SecurityAccount`.  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = AdventureWorks2012.dbo.new_stored_proc ,  
        EXECUTE AS 'SecurityAccount') ;  
```  
  
### <a name="e-setting-the-queue-to-retain-messages"></a>Д. Настройка очереди на хранение сообщений  
 Следующий пример настраивает очередь на хранение сообщений. Очередь хранит все сообщения, отправленные службам или службами, которые используют эту очередь, до тех пор, пока не завершится диалог, который содержит сообщения.  
  
```  
ALTER QUEUE ExpenseQueue WITH RETENTION = ON ;  
```  
  
### <a name="f-removing-activation-from-a-queue"></a>Е. Удаление активации из очереди  
 Следующий пример удаляет все сведения активации из очереди.  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (DROP) ;  
```  
  
### <a name="g-rebuilding-queue-indexes"></a>Ж. Перестроение индексов очереди  
  
**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 В следующем примере перестраиваются индексы очереди  
  
```  
ALTER QUEUE ExpenseQueue REBUILD WITH (MAXDOP = 2)   
```  
  
### <a name="h-reorganizing-queue-indexes"></a>З. Реорганизация индексов очереди  
  
**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Следующий пример перестраивает индексы очереди  
  
```  
ALTER QUEUE ExpenseQueue REORGANIZE   
```  
  
### <a name="i-moving-queue-internal-table-to-another-filegroup"></a>I: перемещения внутренней таблицы очереди в другую файловую группу  
  
**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
ALTER QUEUE ExpenseQueue MOVE TO [NewFilegroup]   
```  
  
## <a name="see-also"></a>См. также  
 [CREATE QUEUE (Transact-SQL)](../../t-sql/statements/create-queue-transact-sql.md)   
 [Удаление ОЧЕРЕДИ &#40; Transact-SQL &#41;](../../t-sql/statements/drop-queue-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
  
