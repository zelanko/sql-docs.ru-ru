---
title: MSSQLSERVER_ 10532 | Документация Майкрософт
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
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 690a5da7eb3ed2da417fc0b5baf53d6668e11f90
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096170"
---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10532|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Невозможно создать структуру плана "%. \*ls поскольку пакет или модуль, указанный параметром `@plan_handle` содержит инструкцию, применимую для структуры плана. Укажите другое значение для параметра `@plan_handle`.|  
  
## <a name="explanation"></a>Объяснение  
 Пакет или модуль, указанный в `@plan_handle`, не содержит инструкцию, подходящую для структуры плана.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите другое значение для параметра `@plan_handle`.  
  
## <a name="see-also"></a>См. также  
 [Руководства планов](../performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
