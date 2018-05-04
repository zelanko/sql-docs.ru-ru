---
title: sp_settriggerorder (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_settriggerorder
- sp_settriggerorder_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_settriggerorder
ms.assetid: 8b75c906-7315-486c-bc59-293ef12078e8
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5059547366dbc167c4c73e3c8cabac53d0007382
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spsettriggerorder-transact-sql"></a>sp_settriggerorder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Указывает триггеры AFTER, срабатывающие первыми или последними. Порядок запуска триггеров AFTER, срабатывающих в промежутке между первым и последним триггерами, не определен.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_settriggerorder [ @triggername = ] '[ triggerschema. ] triggername'   
    , [ @order = ] 'value'   
    , [ @stmttype = ] 'statement_type'   
    [ , [ @namespace = ] { 'DATABASE' | 'SERVER' | NULL } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@triggername=** ] **"**[ *triggerschema ***.**] *аргумент triggername *** "**  
 Имя триггера, порядок срабатывания которого нужно установить или изменить, и схема, которой он принадлежит, если таковая имеется. [*triggerschema ***.**]* аргумент triggername * — **sysname**. Если имя не соответствует триггеру или соответствует триггеру INSTEAD OF, процедура возвращает ошибку. *triggerschema* не может быть указан для триггеров DDL или входа.  
  
 [ **@order=** ] **'***value***'**  
 Новый порядок срабатывания для триггера. *значение* — **varchar(10)** и может принимать одно из следующих значений.  
  
> [!IMPORTANT]  
>  **Первый** и **последний** триггеры должны быть двумя различными триггерами.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Первая**|Триггер срабатывает первым.|  
|**Последняя**|Триггер срабатывает последним.|  
|**None**|Порядок срабатывания триггера не определен.|  
  
 [  **@stmttype=** ] **"***statement_type***"**  
 Указывает инструкцию DDL, которая активирует триггер. *statement_type* — **varchar(50)** и может быть INSERT, UPDATE, DELETE, LOGON или любой [!INCLUDE[tsql](../../includes/tsql-md.md)] события инструкции, перечисленных в [DDL-события](../../relational-databases/triggers/ddl-events.md). Группы событий задавать нельзя.  
  
 Триггер можно назначить в качестве **первый** или **последний** триггер для типа инструкций только после этого его определения в качестве триггера данного типа инструкций. Например, триггер **TR1** можно назначить **первый** для инструкции INSERT в таблице **T1** Если **TR1** определен как триггер INSERT. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Возвращает ошибку, если **TR1**, определенный только как триггер INSERT устанавливается в качестве **первый**, или **последний**, триггер для инструкции UPDATE. Дополнительные сведения см. в разделе «Примечания».  
  
 **@namespace=** { **'DATABASE'** | **«СЕРВЕР»** | NULL}  
 При *аргумент triggername* является триггером DDL **@namespace** указывает, является ли *аргумент triggername* был создан в области базы данных или в области сервера. Если *аргумент triggername* триггером входа необходимо указать сервер. Дополнительные сведения об области действия триггеров DDL см. в разделе [триггеры DDL](../../relational-databases/triggers/ddl-triggers.md). Если не указан или если указано значение NULL, *аргумент triggername* является триггером DML.  
  
||  
|-|  
|SERVER применяет: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
  
## <a name="dml-triggers"></a>Триггеры DML  
 Может быть только один **первый** и один **последний** триггер для каждой инструкции отдельной таблицы.  
  
 Если **первый** на таблицы, базы данных или сервера уже определен первый триггер, нельзя назначить новый триггер как **первый** для таблицы, базы данных или сервера для той же *statement_type* . Это ограничение также применяется **последний** триггеров.  
  
 Репликация автоматически создает первый триггер для любой таблицы, включенной в подписку немедленным обновлением или обновлением с постановкой в очередь. Репликация требует, чтобы ее триггер был первым. При попытке вставить таблицу с указанным первым триггером в немедленно обновляемую подписку или подписку, обновляемую посредством очередей, репликация инициирует ошибку. При попытке сделать триггер первым триггером после включения таблицы в подписку **sp_settriggerorder** возвращает ошибку. Используйте инструкцию ALTER TRIGGER для триггера репликации, или использовать **sp_settriggerorder** Чтобы изменить триггер репликации **последний** или **нет** триггер, подписка не не работает.  
  
## <a name="ddl-triggers"></a>Триггеры DDL  
 Если в том же событии существуют триггер DDL в области базы данных и триггер DDL в области сервера, можно указать, что оба триггера в качестве **первый** триггера или **последний** триггера. Триггеры сервера всегда запускаются в первую очередь. Порядок выполнения триггеров DDL, которые определены для одного события, следующий.  
  
1.  Триггер уровня сервера, обозначенный как **первый**.  
  
2.  Другие триггеры сервера.  
  
3.  Триггер уровня сервера, обозначенный как **последний**.  
  
4.  Триггер уровня базы данных, обозначенный как **первый**.  
  
5.  Другие триггеры базы данных.  
  
6.  Триггер уровня базы данных, обозначенный как **последний**.  
  
## <a name="general-trigger-considerations"></a>Общие соглашения о триггерах  
 Если инструкция ALTER TRIGGER меняет первый или последний триггер, **первый** или **последний** изначально установленный этому триггеру атрибут удаляется и заменяется значение **нет**. Порядок сортировки необходимо сбросить с помощью **sp_settriggerorder**.  
  
 Если тот же триггер необходимо назначить в качестве первого или последнего порядок для нескольких типов инструкций, **sp_settriggerorder** необходимо выполнить для каждого типа инструкций. Кроме того, триггер должен быть сначала определен для типа инструкций, прежде чем он может быть назначен как **первый** или **последний** запуск триггера данного типа инструкций.  
  
## <a name="permissions"></a>Разрешения  
 Чтобы установить порядок запуска триггера DDL сервера (созданного с помощью ON ALL SERVER) или триггера входа, необходимо разрешение CONTROL SERVER.  
  
 Чтобы установить порядок запуска триггера DDL базы данных (созданного с помощью ON DATABASE), необходимо разрешение ALTER ANY DATABASE DDL TRIGGER.  
  
 Чтобы установить порядок запуска триггера DML, необходимо разрешение ALTER на таблицу или представление, для которых этот триггер определен.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-setting-the-firing-order-for-a-dml-trigger"></a>A. Установка порядка срабатывания триггера DML  
 На этом примере показано, как указывается, что триггер `uSalesOrderHeader` должен срабатывать первым после выполнения операции `UPDATE` над таблицей `Sales.SalesOrderHeader`.  
  
```  
USE AdventureWorks2012;  
GO  
sp_settriggerorder @triggername= 'Sales.uSalesOrderHeader', @order='First', @stmttype = 'UPDATE';  
```  
  
### <a name="b-setting-the-firing-order-for-a-ddl-trigger"></a>Б. Установка порядка срабатывания триггера DDL  
 На этом пример показано, как указывается, что триггер `ddlDatabaseTriggerLog` должен срабатывать первым после события `ALTER_TABLE` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
sp_settriggerorder @triggername= 'ddlDatabaseTriggerLog', @order='First', @stmttype = 'ALTER_TABLE', @namespace = 'DATABASE';  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
  
