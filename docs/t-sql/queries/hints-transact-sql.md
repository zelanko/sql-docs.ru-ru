---
title: Указания (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 68d93d1ab8e0c1b9f3592642763123491f9d90d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689632"
---
# <a name="hints-transact-sql"></a>Указания (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Подсказки являются параметрами или стратегиями, указанными для обеспечения выполнения инструкций SELECT, INSERT, UPDATE или DELETE обработчиком запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указания имеют преимущество над любым планом выполнения, который может быть выбран оптимизатором запросов для запроса.  
  
> [!CAUTION]  
>  Так как оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно выбирает наилучший план выполнения для запроса, рекомендуется использовать указания \<join_hint>, \<query_hint> и \<table_hint> в последнюю очередь и только опытным разработчикам и администраторам баз данных.
  
 В этом разделе описаны следующие указания:  
  
-   [Указания в соединении](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Указания запросов](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Табличное указание](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
