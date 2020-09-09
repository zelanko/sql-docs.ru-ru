---
description: sp_settriggerorder (Transact-SQL)
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: da6cb44163370332968c32324086b27f673b3f69
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543074"
---
# <a name="sp_settriggerorder-transact-sql"></a>sp_settriggerorder (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

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
`[ @triggername = ] '[ _triggerschema.] _triggername'` Имя триггера и схема, к которой он принадлежит (если применимо), порядок которого должен быть установлен или изменен. [_тригжерсчема_**.**] *triggername* имеет тип **sysname**. Если имя не соответствует триггеру или соответствует триггеру INSTEAD OF, процедура возвращает ошибку. *тригжерсчема* нельзя указывать для триггеров DDL и logon.  
  
`[ @order = ] 'value'` Параметр для нового порядка триггера. *value* имеет тип **varchar (10)** и может принимать одно из следующих значений.  
  
> [!IMPORTANT]  
>  **Первый** и **последний** триггеры должны быть двумя разными триггерами.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Первая**|Триггер срабатывает первым.|  
|**Последняя**|Триггер срабатывает последним.|  
|**None**|Порядок срабатывания триггера не определен.|  
  
`[ @stmttype = ] 'statement_type'` Указывает инструкцию SQL, которая запускает триггер. *statement_type* имеет тип **varchar (50)** и может использоваться для вставки, обновления, удаления, входа в систему или любого [!INCLUDE[tsql](../../includes/tsql-md.md)] события инструкции, указанного в [DDL-событиях](../../relational-databases/triggers/ddl-events.md). Группы событий задавать нельзя.  
  
 Триггер можно назначить **первым** или **последним** триггером для типа инструкции только после того, как триггер был определен как триггер для этого типа инструкции. Например, триггер **TR1** может быть назначен **первым** для инструкции INSERT в таблице **T1** , если **TR1** определен как триггер INSERT. [!INCLUDE[ssDE](../../includes/ssde-md.md)]Функция возвращает ошибку, если **TR1**, который был определен только как триггер INSERT, устанавливается в качестве **первого**или **последнего**триггера для инструкции UPDATE. Дополнительные сведения см. в разделе "Примечания".  
  
 ** \@ Namespace =** { **' база данных**'  |  **' сервер '** | ЗАКАНЧИВАЮЩ  
 Если *triggername* является триггером DDL, ** \@ пространство имен** указывает, была ли *triggername* создана с областью базы данных или областью сервера. Если *triggername* является триггером входа, необходимо указать Server. Дополнительные сведения об области триггера DDL см. в разделе [триггеры DDL](../../relational-databases/triggers/ddl-triggers.md). Если не указано или указано значение NULL, *triggername* является триггером DML.  
  
* СЕРВЕР применяется к: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздним версиям.
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) и 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
  
## <a name="dml-triggers"></a>Триггеры DML  
 Для каждой инструкции в одной таблице может быть только один **первый** и один **последний** триггер.  
  
 Если **первый** триггер уже определен для таблицы, базы данных или сервера, нельзя назначить новый триггер **первым** для той же таблицы, базы данных или сервера для той же *statement_type*. Это ограничение также применяет **последние** триггеры.  
  
 Репликация автоматически создает первый триггер для любой таблицы, включенной в подписку немедленным обновлением или обновлением с постановкой в очередь. Репликация требует, чтобы ее триггер был первым. При попытке вставить таблицу с указанным первым триггером в немедленно обновляемую подписку или подписку, обновляемую посредством очередей, репликация инициирует ошибку. При попытке сделать триггер первым триггером после включения таблицы в подписку **sp_settriggerorder** возвращает ошибку. При использовании инструкции ALTER TRIGGER для триггера репликации или при использовании **sp_settriggerorder** для изменения триггера репликации на **последний** или **ни один** триггер, подписка работает неправильно.  
  
## <a name="ddl-triggers"></a>Триггеры DDL  
 Если в одном событии существует триггер DDL с областью базы данных и триггер DDL с областью сервера, то можно указать, что оба триггера являются **первым** триггером или **последним** триггером. Триггеры сервера всегда запускаются в первую очередь. Порядок выполнения триггеров DDL, которые определены для одного события, следующий.  
  
1.  Триггер уровня сервера, помеченный как **первый**.  
  
2.  Другие триггеры сервера.  
  
3.  Триггер уровня сервера, помеченный **последним**.  
  
4.  Триггер уровня базы данных, помеченный как **First**.  
  
5.  Другие триггеры базы данных.  
  
6.  Триггер уровня базы данных, помеченный **последним**.  
  
## <a name="general-trigger-considerations"></a>Общие соглашения о триггерах  
 Если инструкция ALTER TRIGGER изменяет первый или последний триггер, **первый** или **последний** атрибут, изначально заданный для триггера, удаляется, а значение заменяется на **None**. Значение порядка должно быть сброшено с помощью **sp_settriggerorder**.  
  
 Если один и тот же триггер должен быть указан в качестве первого или последнего заказа для более чем одного типа инструкции, **sp_settriggerorder** должны выполняться для каждого типа инструкции. Кроме того, триггер необходимо сначала определить для типа инструкции, прежде чем его можно будет назначить **первым** или **последним** триггером для этого типа инструкции.  
  
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
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
  
