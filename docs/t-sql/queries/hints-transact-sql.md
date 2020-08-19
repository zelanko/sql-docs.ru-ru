---
description: Указания (Transact-SQL)
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 16f0e437e864ccb2bd0b4c173b40d84098c51b30
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459204"
---
# <a name="hints-transact-sql"></a>Указания (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Подсказки являются параметрами или стратегиями, указанными для обеспечения выполнения инструкций SELECT, INSERT, UPDATE или DELETE обработчиком запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Указания имеют преимущество над любым планом выполнения, который может быть выбран оптимизатором запросов для запроса.  
  
> [!CAUTION]  
>  Оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно выбирает наилучший план выполнения. Поэтому \<join_hint>, \<query_hint> и \<table_hint> рекомендуется использовать только опытным разработчикам и администраторам баз данных в качестве последнего средства.
  
 В этом разделе описаны следующие указания:  
  
-   [Указания в соединении](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Указания запросов](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Табличное указание](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
