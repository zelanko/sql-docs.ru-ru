---
title: MSSQLSERVER_8712 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 09ad71165e148069fdb07dc42b27f24015a07b52
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180048"
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
  
## <a name="see-also"></a>См. также  
 [Указания запросов (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Руководства планов](../performance/plan-guides.md)  
  
  
