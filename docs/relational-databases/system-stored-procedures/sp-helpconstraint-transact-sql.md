---
title: sp_helpconstraint (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpconstraint
- sp_helpconstraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpconstraint
ms.assetid: 29d6cd36-535d-4765-bca8-62f9d9886ff5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bacf8f0c891e595a775a5e279c5341f3ca0944b1
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535256"
---
# <a name="sphelpconstraint-transact-sql"></a>sp_helpconstraint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает список всех типов ограничений, их пользовательские или предоставляемые системой имена, столбцы, на которых они определены, и выражения, определяющие ограничения (только для ограничений DEFAULT и CHECK).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpconstraint [ @objname = ] 'table'   
     [ , [ @nomsg = ] 'no_message' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'table'` Является таблицей, о которых ограничение возвращаются сведения. Указанная таблица должна находиться в текущей базе данных. *Таблица* — **nvarchar(776)**, не имеет значения по умолчанию.  
  
`[ @nomsg = ] 'no_message'` — Необязательный параметр, который выводит имя таблицы. *no_message* — **varchar(5)**, значение по умолчанию **msg**. **nomsg** подавляет печать.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_helpconstraint** отображает нисходящем порядке индексированный столбец, если он входит в первичные ключи. Нисходящий индексированный столбец представляется в результирующем наборе со знаком минуса (-), стоящим за именем столбца. По умолчанию восходящий индексированный столбец представляется только по своему имени.  
  
## <a name="remarks"></a>Примечания  
 Выполнение **sp_help**_таблицы_ выводятся все сведения об указанной таблице. Для просмотра только данных ограничений используйте **sp_helpconstraint**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показываются все ограничения для таблицы `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpconstraint 'Production.Product';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.CHECK_CONSTRAINTS &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.default_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)  
  
  
