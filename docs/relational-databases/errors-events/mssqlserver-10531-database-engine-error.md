---
title: "MSSQLSERVER_10531 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 7275937bea09abb35dba243c6784aaa551107953
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10531"></a>MSSQLSERVER_10531
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10531|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Не удалось создать структуру плана «%.*ls» из кэша, поскольку пользователь не имеет необходимых разрешений. Предоставьте разрешение VIEW SERVER STATE пользователю, создающему структуру плана.|  
  
## <a name="explanation"></a>Объяснение  
Пользователь не имеет разрешений, необходимых для создания указанной структуры плана из кэша планов.  
  
## <a name="user-action"></a>Действие пользователя  
Предоставьте разрешение VIEW SERVER STATE пользователю, создающему структуру плана.  
  
## <a name="see-also"></a>См. также:  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
