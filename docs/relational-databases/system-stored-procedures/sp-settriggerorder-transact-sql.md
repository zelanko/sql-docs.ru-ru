---
title: sp_settriggerorder (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_settriggerorder
- sp_settriggerorder_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_settriggerorder
ms.assetid: 8b75c906-7315-486c-bc59-293ef12078e8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b9dca1aca3883b16b13f4e0abdb842deaf5bbfdd
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537906"
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
`[ @triggername = ] '[ _triggerschema.] _triggername'` Имя триггера и схемы, к которой он принадлежит, если это применимо, порядок которых нужно задать или изменить. [_triggerschema_**.**] *triggername* — **sysname**. Если имя не соответствует триггеру или соответствует триггеру INSTEAD OF, процедура возвращает ошибку. *triggerschema* нельзя указывать для триггеров DDL или входа.  
  
`[ @order = ] 'value'` Это параметр для нового заказа триггера. *значение* — **varchar(10)** и он может принимать одно из следующих значений.  
  
> [!IMPORTANT]  
>  **Первый** и **последнего** триггеры должны быть двумя различными триггерами.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Первая**|Триггер срабатывает первым.|  
|**Последняя**|Триггер срабатывает последним.|  
|**None**|Порядок срабатывания триггера не определен.|  
  
`[ @stmttype = ] 'statement_type'` Указывает инструкцию SQL, которая активирует триггер. *statement_type* — **varchar(50)** и может быть INSERT, UPDATE, DELETE, LOGON или любой [!INCLUDE[tsql](../../includes/tsql-md.md)] события инструкции, перечисленные в [DDL-события](../../relational-databases/triggers/ddl-events.md). Группы событий задавать нельзя.  
  
 Триггер может быть назначен в качестве **первый** или **последнего** триггер для типа инструкции только после этого триггера был определен как триггер для данного типа инструкций. Например, триггер **TR1** может быть назначен **первый** для инструкции INSERT в таблице **T1** Если **TR1** определен как триггер INSERT. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Возвращает сообщение об ошибке, если **TR1**, определенный только как триггер INSERT задан в качестве **первый**, или **последнего**, триггер для инструкции UPDATE. Дополнительные сведения см. в разделе «Примечания».  
  
 **@namespace=** { **«DATABASE»** | **«СЕРВЕР»** | NULL}  
 Когда *triggername* является триггером DDL, **@namespace** указывает ли *triggername* был создан с помощью области базы данных или в области сервера. Если *triggername* является триггером входа, необходимо указать сервер. Дополнительные сведения о область действия триггера DDL, см. в разделе [триггеры DDL](../../relational-databases/triggers/ddl-triggers.md). Если не указан или если указано значение NULL, *triggername* является триггером DML.  
  
||  
|-|  
|SERVER применяет: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
  
## <a name="dml-triggers"></a>Триггеры DML  
 Может существовать только один **первый** и один **последнего** триггер для каждой инструкции отдельной таблицы.  
  
 Если **первый** на таблицы, базы данных или сервера уже определен триггер, нельзя назначить новый триггер как **первый** для той же таблице, базы данных или сервера для того же *statement_type* . Это ограничение также применяется **последнего** триггеров.  
  
 Репликация автоматически создает первый триггер для любой таблицы, включенной в подписку немедленным обновлением или обновлением с постановкой в очередь. Репликация требует, чтобы ее триггер был первым. При попытке вставить таблицу с указанным первым триггером в немедленно обновляемую подписку или подписку, обновляемую посредством очередей, репликация инициирует ошибку. При попытке сделать триггер первым триггером после включения таблицы в подписку **sp_settriggerorder** возвращает ошибку. Если вы используете ALTER TRIGGER для триггера репликации, или **sp_settriggerorder** чтобы сделать триггер репликации для **последнего** или **None** триггера, подписка не не работает.  
  
## <a name="ddl-triggers"></a>Триггеры DDL  
 Если на того же события существуют триггер DDL в области базы данных и триггер DDL в области сервера, можно указать, что оба триггера в качестве **первый** триггера или **последнего** триггера. Триггеры сервера всегда запускаются в первую очередь. Порядок выполнения триггеров DDL, которые определены для одного события, следующий.  
  
1.  Триггер уровня сервера, обозначенный как **первый**.  
  
2.  Другие триггеры сервера.  
  
3.  Триггер уровня сервера, обозначенный как **последнего**.  
  
4.  Триггер уровня базы данных, обозначенный как **первый**.  
  
5.  Другие триггеры базы данных.  
  
6.  Триггер уровня базы данных, обозначенный как **последнего**.  
  
## <a name="general-trigger-considerations"></a>Общие соглашения о триггерах  
 Если инструкция ALTER TRIGGER меняет первый или последний триггер, **первый** или **последнего** атрибутов, изначально установленный этому триггеру удаляется и заменяется значение **None**. Порядок сортировки должен быть изменен с помощью **sp_settriggerorder**.  
  
 Если тот же триггер необходимо назначить в качестве первого или последнего порядок для нескольких типов инструкций, **sp_settriggerorder** необходимо выполнить для каждого типа инструкций. Кроме того, триггер должен быть сначала определен для типа, прежде чем он может быть назначен в качестве **первый** или **последнего** триггер, подлежащий данного типа инструкций.  
  
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
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
  
