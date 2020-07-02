---
title: sp_refreshview (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refreshview
- sp_refreshview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refreshview
ms.assetid: 9ce1d07c-ee66-4a83-8c73-cd2cc104dd08
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bd963a39dddaca5cd2558ea95853fdebf366e2ee
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719226"
---
# <a name="sp_refreshview-transact-sql"></a>sp_refreshview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Обновляет метаданные для заданного, не привязанного к схеме, представления. Постоянные метаданные представления могут устареть вследствие изменения базовых объектов, от которых зависит представление.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_refreshview [ @viewname = ] 'viewname'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @viewname = ] 'viewname'`Имя представления. *ViewName* имеет тип **nvarchar**и не имеет значения по умолчанию. *ViewName* может быть составным идентификатором, но может ссылаться только на представления в текущей базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Если представление не создано с параметром SCHEMABINDING, то **sp_refreshview** должны выполняться при внесении изменений в объекты, лежащие в основе представления, влияющие на определение представления. В противном случае результат запроса представления может быть непредвиденным.  
  
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
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_refreshsqlmodule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md)  
  
  
