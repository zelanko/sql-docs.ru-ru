---
title: "MSSQLSERVER_8712 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: c8d97513694a8f1b0559dbd029a6f9f3bed91cf5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8712|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|USEPLAN_ERR_NO_INDEX|  
|Текст сообщения|Индекс «%.*ls», заданный в указании USE PLAN, не существует. Укажите существующий индекс или создайте индекс с указанным именем.|  
  
## <a name="explanation"></a>Объяснение  
Индекс, заданный в указании USE PLAN, не существует.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь в том, что существуют все индексы, которые заданы в указании USE PLAN.  
  
## <a name="see-also"></a>См. также:  
[Указания запросов (Transact-SQL)](~/t-sql/queries/hints-transact-sql-query.md)  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
  
