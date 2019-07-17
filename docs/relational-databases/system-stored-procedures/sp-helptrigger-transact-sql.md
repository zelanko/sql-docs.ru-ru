---
title: sp_helptrigger (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1e6244443fc1f6ba7d83376226fedd56563e0d39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048220"
---
# <a name="sphelptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает тип или типы триггеров DML, определенных в указанной таблице для текущей базы данных. sp_helptrigger нельзя использовать с триггерами DDL. Запрос [системные хранимые процедуры](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) вместо этого представление каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @tabname = ] 'table'` — Имя таблицы в текущей базе данных, для которого необходимо вернуть сведения о триггерах. *Таблица* — **nvarchar(776)** , не имеет значения по умолчанию.  
  
`[ @triggertype = ] 'type'` — Это тип триггера DML для получения информации о. *Тип* — **char(6)** , значение по умолчанию NULL, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**DELETE**|Возвращает сведения о триггере DELETE.|  
|**INSERT**|Возвращает сведения о триггере INSERT.|  
|**UPDATE**|Возвращает сведения о триггере UPDATE.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Следующая таблица показывает данные в результирующем наборе.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**sysname**|Имя триггера.|  
|**trigger_owner**|**sysname**|Имя владельца таблицы, для которой определен триггер.|  
|**isupdate**|**int**|1=триггер UPDATE<br /><br /> 0=не триггер UPDATE|  
|**isdelete**|**int**|1=триггер DELETE<br /><br /> 0=не триггер DELETE|  
|**isinsert**|**int**|1=триггер INSERT<br /><br /> 0=не триггер INSERT|  
|**isafter**|**int**|1=триггер AFTER<br /><br /> 0=не триггер AFTER|  
|**isinsteadof**|**int**|1=триггер INSTEAD OF<br /><br /> 0=не триггер INSTEAD OF|  
|**столбец trigger_schema**|**sysname**|Имя схемы, к которой принадлежит триггер.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md) разрешение на таблицу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется хранимая процедура `sp_helptrigger` для получения сведений о триггерах для таблицы `Person.Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
