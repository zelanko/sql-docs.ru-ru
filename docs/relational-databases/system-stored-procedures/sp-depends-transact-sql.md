---
title: sp_depends (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_depends
- sp_depends_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_depends
ms.assetid: d9934590-c6ae-4936-91c3-146055ef2c57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ee6b9df37e61dcb4eed45bc11431d49b160cf87
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053100"
---
# <a name="sp_depends-transact-sql"></a>sp_depends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о зависимостях объектов базы данных, таких как представления и процедуры, зависящие от таблицы или представления, а также таблицы и представления, зависящие от представления или процедуры. О ссылках на объекты вне текущей базы данных не сообщается.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте представление [sys. dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md) и [sys. dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_depends [ @objname = ] '<object>'   
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name.  
    object_name  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных.  
  
 *schema_name*  
 Имя схемы, которой принадлежит объект.  
  
 *object_name*  
 Имя объекта базы данных, который проверяется на зависимости. Объект может быть таблицей, представлением, хранимой процедурой, определяемой пользователем функцией или триггером. o*bject_name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_depends** отображает два результирующих набора.  
  
 Следующий результирующий набор показывает объекты, от которых * \<зависит объект>* .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|Имя элемента, для которого существует зависимость.|  
|**type**|**nvarchar (16)**|Тип элемента.|  
|**модернизирован**|**nvarchar (7)**|Был ли элемент обновлен.|  
|**выбрать**|**nvarchar (8)**|Используется ли объект в инструкции SELECT.|  
|**рубрик**|**имеет sysname**|Столбец или параметр, от которого существует зависимость.|  
  
 Следующий результирующий набор показывает объекты, зависящие от * \<>объектов *.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|Имя элемента, для которого существует зависимость.|  
|**type**|**nvarchar (16)**|Тип элемента.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-dependencies-on-a-table"></a>A. Список зависимостей таблицы  
 Следующий пример отображает список объектов базы данных, которые зависят от таблицы `Sales.Customer` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Заданы как имя схемы, так и имя таблицы.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_depends @objname = N'Sales.Customer' ;  
```  
  
### <a name="b-listing-dependencies-on-a-trigger"></a>Б. Список зависимостей триггера  
 Следующий пример отображает объекты базы данных, от которых зависит триггер `iWorkOrder`.  
  
```  
EXEC sp_depends @objname = N'AdventureWorks2012.Production.iWorkOrder' ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ВЫПОЛНЕНИЕ &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys. sql_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
