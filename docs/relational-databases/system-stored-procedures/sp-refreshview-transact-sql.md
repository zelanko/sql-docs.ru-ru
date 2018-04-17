---
title: sp_refreshview (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_refreshview
- sp_refreshview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refreshview
ms.assetid: 9ce1d07c-ee66-4a83-8c73-cd2cc104dd08
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f82432aa08e19f0c2174943fd1b2aa3ed9f5c407
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sprefreshview-transact-sql"></a>sp_refreshview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет метаданные для заданного, не привязанного к схеме, представления. Постоянные метаданные представления могут устареть вследствие изменения базовых объектов, от которых зависит представление.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_refreshview [ @viewname = ] 'viewname'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@viewname=** ] **"***viewname***"**  
 Имя представления. *ViewName* — **nvarchar**, не имеет значения по умолчанию. *ViewName* может являться составным идентификатором, однако может обращаться только к представлениям в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Если представление создано без использования предложения schemabinding, **sp_refreshview** следует запускать при изменении базовых объектов представления, влияющих на определение представления. В противном случае результат запроса представления может быть непредвиденным.  
  
## <a name="permissions"></a>Разрешения  
 Требуются разрешение ALTER для представления и разрешение REFERENCES для определяемых пользователями типов данных среды CLR и коллекций XML-схем, на которые ссылаются столбцы представления.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-updating-the-metadata-of-a-view"></a>A. Обновление метаданных представления  
 В следующем примере выполняется обновление метаданных представления `Sales.vIndividualCustomer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sp_refreshview N'Sales.vIndividualCustomer';  
```  
  
### <a name="b-creating-a-script-that-updates-all-views-that-have-dependencies-on-a-changed-object"></a>Б. Создание скрипта, обновляющего все представления с зависимостями от измененного объекта  
 Предполагается, что таблица `Person.Person` была изменена таким образом, что это повлияло на определение созданных на ней представлений. В следующем примере создается скрипт, обновляющий метаданные для всех представлений с зависимостями от таблицы `Person.Person`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT 'EXEC sp_refreshview ''' + name + ''''   
FROM sys.objects AS so   
INNER JOIN sys.sql_expression_dependencies AS sed   
    ON so.object_id = sed.referencing_id   
WHERE so.type = 'V' AND sed.referenced_id = OBJECT_ID('Person.Person');  
```  
  
## <a name="see-also"></a>См. также  
 [Компонент Database Engine хранимой процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_refreshsqlmodule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md)  
  
  
