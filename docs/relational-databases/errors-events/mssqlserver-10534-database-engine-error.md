---
title: "MSSQLSERVER_10534 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10534 (Database Engine error)
ms.assetid: e65bb118-99d5-4fdb-b1d5-0ec70f0a677b
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: bbe174e84fdf7957986b669a1c25b32369427c69
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10534"></a>MSSQLSERVER_10534
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10534|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INVALID_PARAMS|  
|Текст сообщения|Не удается создать структуру плана "%.\*ls", поскольку задано недопустимое значение параметра **@params**. Задайте значение в форме *имя_параметра тип_параметра* или укажите значение NULL.|  
  
## <a name="explanation"></a>Объяснение  
Значение, указанное для **@params**, недопустимо.  
  
## <a name="user-action"></a>Действие пользователя  
Задайте значение в форме *имя_параметра тип_параметра* или укажите значение NULL.  
  
## <a name="see-also"></a>См. также:  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
