---
title: MSSQLSERVER_ 10536 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00ca6874fc2b46c1b01495c5c7a0808265b0dd77
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428953"
---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10536|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_TOO_MANY_STMTS|  
|Текст сообщения|Невозможно создать структуру плана "%. \*ls поскольку пакет или модуль, соответствующий указанному `@plan_handle` содержит более 1000 подходящих инструкций. Создайте структуру плана для каждой инструкции в пакете или модуле, указав для каждой инструкции значение `statement_start_offset`.|  
  
## <a name="explanation"></a>Объяснение  
 Пакет или модуль, соответствующий указанному дескриптору `@plan_handle`, содержит больше 1000 подходящих инструкций.  
  
## <a name="user-action"></a>Действие пользователя  
 Создайте структуру плана для каждой инструкции в пакете или модуле, указав для каждой инструкции значение `statement_start_offset`.  
  
## <a name="see-also"></a>См. также  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
