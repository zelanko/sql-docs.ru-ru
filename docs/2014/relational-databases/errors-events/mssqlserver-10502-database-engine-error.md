---
title: MSSQLSERVER_10502 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10502 (Database Engine error)
ms.assetid: 26d9b64d-4299-4b55-92d0-0a32a3688c0a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 42b4a39678e4b85e581bca7e1b9e085c6f4620f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62870676"
---
# <a name="mssqlserver10502"></a>MSSQLSERVER_10502
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10502|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_DUP_FOUND|  
|Текст сообщения|Не удается создать структуру плана "%.*ls", так как инструкция, указанная параметрами @stmt и @module_or_batch или параметрами @plan_handle и @statement_start_offset, соответствует существующей структуре плана "%.\*ls" в базе данных. Перед созданием новой структуры плана удалите существующую.|  
  
## <a name="explanation"></a>Объяснение  
 Для указанной инструкции существует структура плана.  
  
## <a name="user-action"></a>Действие пользователя  
 Перед созданием новой структуры плана удалите существующую.  
  
## <a name="see-also"></a>См. также  
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
