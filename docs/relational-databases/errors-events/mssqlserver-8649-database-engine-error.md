---
title: "MSSQLSERVER_8649 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4bea16bdc86c935da1b95adf52290234710e0b21
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8649|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|COST_TOO_HIGH|  
|Текст сообщения|Запрос %d был отменен, потому что расчетные затраты на его выполнение превышают установленный порог в %d. Свяжитесь с системным администратором.|  
  
## <a name="explanation"></a>Объяснение  
Запрос был отменен, потому что расчетные затраты на его выполнение превысили установленный параметром QUERY_GOVERNOR_COST_LIMIT порог.  
  
## <a name="user-action"></a>Действие пользователя  
Установите более высокое значение параметра QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="see-also"></a>См. также:  
[SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  

