---
title: "MSSQLSERVER_8710 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f96172d7cb0ae2eddd1da57fd3caebf527270fae
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|8710|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Текст сообщения|Агрегатные функции, используемые в запросах CUBE, ROLLUP или GROUPING SET, должны обеспечивать возможность слияния подытогов. Чтобы решить эту проблему, удалите агрегатную функцию или напишите запрос UNION ALL с предложениями GROUP BY.|  
  
## <a name="explanation"></a>Объяснение  
В запросе CUBE, ROLLUP или GROUPING SETS была использована агрегатная функция, не предусматривающая метод для слияния подытогов.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы решить эту проблему, удалите агрегатную функцию или напишите запрос UNION ALL с предложениями GROUP BY.  
  
