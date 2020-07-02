---
title: Объект SqlTriggerContext | Документация Майкрософт
description: В SQL Server интеграции со средой CLR класс SqlTriggerContext предоставляет сведения о контексте для триггера, включая тип действия и столбцов, измененных в операции.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlTriggerContext object
- triggers [CLR integration]
- context [CLR integration]
ms.assetid: 472a2d0b-64ae-4877-8f11-a5620aa698b7
author: rothja
ms.author: jroth
ms.openlocfilehash: 4634a0c95e64516b6364fbfd68edeb9cd6156511
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765416"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext, объект
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Класс **SqlTriggerContext** предоставляет сведения контекста о триггере. В сведения о контексте включают тип действия, вызвавшего срабатывание триггера, столбцы, измененные в рамках операции UPDATE, а в случае триггера DDL — структуру XML **EventData** , которая описывает операцию триггера. Дополнительные сведения и примеры использования класса **SqlTriggerContext** см. в разделе [триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
 Дополнительные сведения см. в справочной документации по классу **Microsoft. SqlServer. Server. SqlTriggerContext** в документации по .NET Framework SDK.  
  
## <a name="see-also"></a>См. также  
 [Триггеры CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
