---
title: "MSSQLSERVER_10520 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 05acd414289507544caa7ae5806471982768949e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10520|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_PARAM_NOT_ALLOWED|  
|Текст сообщения|Не удается создать структуру плана '%.*ls', поскольку для параметра @type указано значение '%!s', а для параметра '%!s' указано значение, отличное от NULL. Для заданного типа этот параметр должен иметь значение NULL. Укажите для этого параметра значение NULL либо измените его тип таким образом, чтобы он допускал значение, отличное от NULL.|  
  
## <a name="explanation"></a>Объяснение  
Для типа, указанного в @type, требуется значение NULL, но предоставлено значение, отличное от NULL.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите для этого параметра значение NULL либо измените его тип таким образом, чтобы он допускал значение, отличное от NULL.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
  
