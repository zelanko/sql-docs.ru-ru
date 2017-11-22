---
title: "Указания (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 30a221dbe557704085fe280b36d2b762ec15f231
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="hints-transact-sql"></a>Указания (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Подсказки являются параметрами или стратегиями, указанными для обеспечения выполнения инструкций SELECT, INSERT, UPDATE или DELETE обработчиком запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указания имеют преимущество над любым планом выполнения, который может быть выбран оптимизатором запросов для запроса.  
  
> [!CAUTION]  
>  Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оптимизатор запросов обычно выбирает наилучший план выполнения для запроса, рекомендуется \<join_hint >, \<query_hint >, и \<table_hint > будет использоваться только в качестве последнего средства опытным Разработчики и Администраторы баз данных.
  
 В этом разделе описаны следующие указания:  
  
-   [Указания в соединении](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Указания запросов](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Табличная подсказка](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
