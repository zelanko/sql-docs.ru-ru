---
title: "SqlTriggerContext, объект | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27a4a1e0a7fecccab1b61c29d7be82f9a1d4b047
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext, объект
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]**SqlTriggerContext** предоставляет сведения контекста о триггере. В сведения о контексте включают тип действия, вызвавшего срабатывание триггера, столбцы, измененные в рамках операции UPDATE, а в случае триггера DDL — структуру XML **EventData** , которая описывает операцию триггера. Дополнительные сведения и примеры использования **SqlTriggerContext** см. в описании [триггеры CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
 Дополнительные сведения см. в справочной документации по классу **Microsoft.SqlServer.Server.SqlTriggerContext** пакета .NET Framework SDK.  
  
## <a name="see-also"></a>См. также:  
 [Триггеры CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
