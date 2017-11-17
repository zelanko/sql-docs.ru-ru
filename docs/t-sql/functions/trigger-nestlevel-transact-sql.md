---
title: "Функция TRIGGER_NESTLEVEL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRIGGER_NESTLEVEL
- TRIGGER_NESTLEVEL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- triggers [SQL Server], number executed
- number of triggers
- TRIGGER_NESTLEVEL function
ms.assetid: 6a33e74a-0cf9-4ae1-a1e4-4a137a3ea39d
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 352ea0e82fa853639d94a6a151b3d7df5f5b2f21
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="triggernestlevel-transact-sql"></a>TRIGGER_NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает число обработчиков, выполненных при срабатывании триггера инструкции. Функция TRIGGER_NESTLEVEL используется в триггерах DML и DDL для определения текущего уровня вложенности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TRIGGER_NESTLEVEL ( [ object_id ] , [ 'trigger_type' ] , [ 'trigger_event_category' ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор объекта триггера. Если *object_id* указано, сколько раз был выполнен указанный триггер для инструкции, возвращается. Если *object_id* не указано, сколько раз были выполнены все триггеры для инструкции, возвращается.  
  
 **"** *trigger_type* **"**  
 Указывает, к каким триггерам применяется функция TRIGGER_NESTLEVEL — AFTER или INSTEAD OF. Укажите **AFTER** для триггеров AFTER. Укажите **IOT** для триггеров INSTEAD OF. Если *trigger_type* указано, *trigger_event_category* также должен быть указан.  
  
 **"** *trigger_event_category* **"**  
 Указывает, к каким триггерам применять функцию TRIGGER_NESTLEVEL — DML или DDL. Укажите **DML** для триггеров DML. Укажите **DDL** для триггеров DDL. Если *trigger_event_category* указано, *trigger_type* также должен быть указан. Обратите внимание, что только **AFTER** может указываться с **DDL**, так как триггеры DDL можно только триггеров AFTER.  
  
## <a name="remarks"></a>Замечания  
 Если не задано никаких аргументов, функция TRIGGER_NESTLEVEL возвращает общее число триггеров в стеке вызова. Этот список также включает и саму функцию TRIGGER_NESTLEVEL. Пропуск аргументов может наблюдаться в случае, когда триггер выполняет команды, приводящие к запуску другого триггера, или создает последовательность запускаемых триггеров.  
  
 Чтобы получить общее число триггеров в стеке вызовов для конкретного триггер типа и категории событий, укажите *object_id* = 0.  
  
 Функция TRIGGER_NESTLEVEL возвращает 0 в случае выполнения вне триггера, если значение хотя бы одного из аргументов не равно NULL.  
  
 Если каким-либо аргументам явно задано значение NULL, то оно возвращается независимо от того, внутри или вне триггера использовалась функция TRIGGER_NESTLEVEL.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-testing-the-nesting-level-of-a-specific-dml-trigger"></a>A. Проверка уровня вложенности конкретного триггера DML  
  
```  
IF ( (SELECT TRIGGER_NESTLEVEL( OBJECT_ID('xyz') , 'AFTER' , 'DML' ) ) > 5 )  
   RAISERROR('Trigger xyz nested more than 5 levels.',16,-1)  
```  
  
### <a name="b-testing-the-nesting-level-of-a-specific-ddl-trigger"></a>Б. Проверка уровня вложенности конкретного триггера DDL  
  
```  
IF ( ( SELECT TRIGGER_NESTLEVEL ( ( SELECT object_id FROM sys.triggers  
WHERE name = 'abc' ), 'AFTER' , 'DDL' ) ) > 5 )  
   RAISERROR ('Trigger abc nested more than 5 levels.',16,-1)  
```  
  
### <a name="c-testing-the-nesting-level-of-all-triggers-executed"></a>В. Проверка уровня вложенности всех сработавших триггеров  
  
```  
IF ( (SELECT trigger_nestlevel() ) > 5 )  
   RAISERROR  
      ('This statement nested over 5 levels of triggers.',16,-1)  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  

