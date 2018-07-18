---
title: Объект SqlTriggerContext | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ff176908a3ef66f9c1d14d1c5a695932075e8735
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353276"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext, объект
  Класс `SqlTriggerContext` предоставляет сведения контекста о триггере. В сведения о контексте включают тип действия, вызвавшего срабатывание триггера, столбцы, измененные в рамках операции UPDATE, а в случае триггера DDL — структуру XML `EventData`, которая описывает операцию триггера. Дополнительные сведения и примеры использования `SqlTriggerContext` , представлена в разделе [триггеры CLR](../../database-engine/dev-guide/clr-triggers.md).  
  
 Дополнительные сведения см. в справочной документации по классу `Microsoft.SqlServer.Server.SqlTriggerContext` в документации по пакету .NET Framework SDK.  
  
## <a name="see-also"></a>См. также  
 [Триггеры CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
