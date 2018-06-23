---
title: MSSQLSERVER_10521 | Документация Майкрософт
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
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 209496ac8159eb32c36fcded35992cac1e45d6f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187774"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10521|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_PARAM_NEEDED|  
|Текст сообщения|Невозможно создать структуру плана "%. \*ls поскольку `@type` был указан как «%ls» и параметр «%ls» имеет значение NULL. Этот тип должен иметь значение, отличное от NULL, для этого параметра. Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.|  
  
## <a name="explanation"></a>Объяснение  
 Для типа, указанного в `@type`, требуется значение указанного параметра, отличное от NULL, но задано значение NULL.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.  
  
## <a name="see-also"></a>См. также  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Руководства планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
