---
title: "sp_recompile (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_recompile_TSQL
- sp_recompile
dev_langs: TSQL
helpviewer_keywords: sp_recompile
ms.assetid: 6192ca87-febd-4075-8199-14b4fa609b8c
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e802de07e5113d9cf12ba65df56153646361f715
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sprecompile-transact-sql"></a>sp_recompile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Влечет перекомпиляцию при следующем выполнении хранимых процедур, триггеров и функций, определяемых пользователем. Для этого из кэша процедур удаляется существующий план, в результате чего при следующем запуске процедуры или триггера создается новый план. В коллекции [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] вместо события SP:Recompile в журнал записывается событие SP:CacheInsert.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
  
sp_recompile [ @objname = ] 'object'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @objname=] '*объекта*"  
 Уточненное или не уточненное имя хранимой процедуры, триггера, таблица, представления или определяемой пользователем функции в текущей базе данных. *Объект* — **nvarchar(776)**, не имеет значения по умолчанию. Если *объекта* имя хранимой процедурой, триггером или определяемой пользователем функции, хранимой процедуры, триггера или функция будут перекомпилированы при следующем запуске. Если *объекта* имя таблицы или представления, хранимые процедуры, триггеры или определяемые пользователем функции, которые ссылаются на таблицу или представление, будут перекомпилированы при очередном запуске.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или ненулевое значение (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_recompile ищет объект только в текущей базе данных.  
  
 Запросы, используемые хранимыми процедурами или триггерами и определяемые пользователем функции оптимизируются только после их компиляции. Как только индексы или другие изменения, которые влияют на статистику, внесены в базу данных, компилированные хранимые процедуры, триггеры и определяемые пользователем функции могут утратить эффективность. Путем перекомпиляции хранимых процедур и триггеров, влияющих на таблицу, можно повторно оптимизировать запросы.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически перекомпилирует хранимые процедуры, триггеры и определяемые пользователем функции при благоприятном для этого моменте.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER для объекта.  
  
## <a name="examples"></a>Примеры  
 Следующий пример влечет перекомпиляцию хранимых процедур, триггеров и определяемых пользователем функций, которые влияют на таблицу `Customer` , при следующем их выполнении.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
