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
ms.openlocfilehash: c6f11eda2ef791eb8c987af8d82149507770d47a
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809167"
---
# <a name="sqltriggercontext-object"></a>SqlTriggerContext, объект
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Класс **SqlTriggerContext** предоставляет сведения контекста о триггере. В сведения о контексте включают тип действия, вызвавшего срабатывание триггера, столбцы, измененные в рамках операции UPDATE, а в случае триггера DDL — структуру XML **EventData** , которая описывает операцию триггера. Дополнительные сведения и примеры использования класса **SqlTriggerContext** см. в разделе [триггеры CLR](/dotnet/framework/data/adonet/sql/clr-triggers).  
  
 Дополнительные сведения см. в справочной документации по классу **Microsoft. SqlServer. Server. SqlTriggerContext** в документации по .NET Framework SDK.  
  
## <a name="see-also"></a>См. также:  
 [Триггеры CLR](/dotnet/framework/data/adonet/sql/clr-triggers)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
