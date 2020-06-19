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
ms.openlocfilehash: 0ec584649842f787b1de9d2ea6d161aea6970250
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84947774"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10519|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Текст сообщения|Не удается создать структуру плана "%.\*ls", поскольку указания, заданные в параметре `@hints`, нельзя применить к инструкции, заданной параметром `@stmt` или `@statement_start_offset`. Убедитесь, что заданные указания можно применить к этой инструкции.|  
  
## <a name="explanation"></a>Объяснение  
 Указания, заданные в параметре `@hints`, не могут быть применены к инструкции, заданной с помощью `@stmt` или `@statement_start_offset`.  
  
## <a name="user-action"></a>Действие пользователя  
 Задайте указания, которые могут быть применены к этой инструкции.  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
