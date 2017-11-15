---
title: "MSSQLSERVER_10507 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 9c5ed7e253260e2ffe773fc49968737acd14232c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10507|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_STMT_DOES_NOT_MATCH|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", поскольку инструкция, указанная параметрами **@stmt** и **@module_or_batch** или параметрами **@plan_handle** и **@statement_start_offset**, не соответствует ни одной инструкции в указанном модуле или пакете. Измените значения параметров таким образом, чтобы они соответствовали инструкции в модуле или пакете.|  
  
## <a name="explanation"></a>Объяснение  
Инструкция в указанном модуле или пакете не соответствует указанной инструкцией или с величиной смещения инструкции.  
  
## <a name="user-action"></a>Действие пользователя  
Измените указанные значения параметров, чтобы они соответствовали инструкции в модуле или пакете.  
  
## <a name="see-also"></a>См. также:  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
