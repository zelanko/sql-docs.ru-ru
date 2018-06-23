---
title: MSSQLSERVER_8649 | Документация Майкрософт
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
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: 15
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3da65279260e142385a7b872c7234cb0f0b6bc8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095213"
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
  
## <a name="see-also"></a>См. также  
 [SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
