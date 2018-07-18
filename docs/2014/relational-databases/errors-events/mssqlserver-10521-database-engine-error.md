---
title: MSSQLSERVER_10521 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18d823ff21a38c3eeee8df725c9a38172080d40e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421083"
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
|Текст сообщения|Невозможно создать структуру плана "%. \*ls поскольку `@type` был указан как «%ls», а параметр «%ls» имеет значение NULL. Этот тип должен иметь значение, отличное от NULL, для этого параметра. Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.|  
  
## <a name="explanation"></a>Объяснение  
 Для типа, указанного в `@type`, требуется значение указанного параметра, отличное от NULL, но задано значение NULL.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.  
  
## <a name="see-also"></a>См. также  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
