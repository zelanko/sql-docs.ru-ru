---
title: MSSQLSERVER_8649 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b39ed0d8ffe5f7f601b6cb1393596d0d6546e557
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85031777"
---
# <a name="mssqlserver_8649"></a>MSSQLSERVER_8649
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
 [SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)  
  
  
