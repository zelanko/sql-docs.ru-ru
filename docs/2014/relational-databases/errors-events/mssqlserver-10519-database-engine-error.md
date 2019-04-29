---
title: MSSQLSERVER_10519 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6bb9c6f7fddc9ba0d4430b42ba5472a59c29e3cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916239"
---
# <a name="mssqlserver10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10519|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Текст сообщения|Невозможно создать структуру плана "%. \*ls поскольку указания, заданные в `@hints` не может использоваться для инструкции, заданной с помощью `@stmt` или `@statement_start_offset`. Убедитесь, что заданные указания можно применить к этой инструкции.|  
  
## <a name="explanation"></a>Объяснение  
 Указания, заданные в параметре `@hints`, не могут быть применены к инструкции, заданной с помощью `@stmt` или `@statement_start_offset`.  
  
## <a name="user-action"></a>Действие пользователя  
 Задайте указания, которые могут быть применены к этой инструкции.  
  
## <a name="see-also"></a>См. также  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
