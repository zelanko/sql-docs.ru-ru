---
title: sp_helptrigger (Transact-SQL) | Документы Microsoft
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
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6046d4ceb501c6e0ce6f267d29a9f10964861e8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sphelptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает тип или типы триггеров DML, определенных в указанной таблице для текущей базы данных. sp_helptrigger нельзя использовать с триггерами DDL. Запрос [системные хранимые процедуры](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@tabname=** ] **"***таблицы***"**  
 Имя таблицы в текущей базе данных, для которой необходимо вернуть сведения о триггерах. *Таблица* — **nvarchar(776)**, не имеет значения по умолчанию.  
  
 [  **@triggertype=** ] **"***типа***"**  
 Тип триггера DML, о котором необходимо вернуть сведения. *Тип* — **char(6)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
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
|**trigger_schema**|**sysname**|Имя схемы, к которой принадлежит триггер.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется [настроек видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md) разрешение на таблицу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется хранимая процедура `sp_helptrigger` для получения сведений о триггерах для таблицы `Person.Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
