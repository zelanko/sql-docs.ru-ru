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
manager: craigg
ms.openlocfilehash: 5e265344d3e05081ebc01f5e9f7fdd240d27c7d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210504"
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
  
  
