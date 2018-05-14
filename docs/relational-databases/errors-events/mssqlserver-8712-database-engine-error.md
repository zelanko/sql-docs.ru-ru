---
title: MSSQLSERVER_8712 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fdd6aaa98a9a36ff46ef0580af3cf66a6baf594c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
