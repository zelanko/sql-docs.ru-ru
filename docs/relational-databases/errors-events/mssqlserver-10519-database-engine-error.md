---
title: MSSQLSERVER_10519 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7169ed83c3f602a17994e023d1da8ba5c17f94b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver10519"></a>MSSQLSERVER_10519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10519|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Текст сообщения|Не удается создать структуру плана "%.\*ls", поскольку указания, заданные в параметре **@hints**, нельзя применить к инструкции, заданной параметром **@stmt** или **@statement_start_offset**. Убедитесь, что заданные указания можно применить к этой инструкции.|  
  
## <a name="explanation"></a>Объяснение  
Указания, заданные в параметре **@hints**, не могут быть применены к инструкции, заданной с помощью **@stmt** или **@statement_start_offset**.  
  
## <a name="user-action"></a>Действие пользователя  
Задайте указания, которые могут быть применены к этой инструкции.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
