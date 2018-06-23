---
title: SqlTriggerContext, объект | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dbdaefa1e3c5e1c5a53cd6179f4b96320434dbdf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095223"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext, объект
  Класс `SqlTriggerContext` предоставляет сведения контекста о триггере. В сведения о контексте включают тип действия, вызвавшего срабатывание триггера, столбцы, измененные в рамках операции UPDATE, а в случае триггера DDL — структуру XML `EventData`, которая описывает операцию триггера. Дополнительные сведения и примеры использования `SqlTriggerContext` см. в описании [триггеры CLR](../../database-engine/dev-guide/clr-triggers.md).  
  
 Дополнительные сведения см. в справочной документации по классу `Microsoft.SqlServer.Server.SqlTriggerContext` в документации по пакету .NET Framework SDK.  
  
## <a name="see-also"></a>См. также  
 [Триггеры CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
