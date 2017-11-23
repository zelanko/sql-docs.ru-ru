---
title: "Определяемые пользователем статистические функции CLR | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ead22c2cabcc2cfdb42bc6bc44da788ca6b4882c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="clr-user-defined-aggregates"></a>Пользовательские агрегатные функции среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Агрегатные функции выполняют вычисление на наборе значений и возвращают одиночное значение. В большинстве случаев [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживала только встроенные агрегатные функции, такие как **сумма** или **MAX**, работать с набором входных скалярных величин и создавать единое Агрегированное значение из этого набора. Но теперь интеграция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со средой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR позволяет создавать в управляемом коде пользовательские агрегатные функции и предоставлять доступ к ним из [!INCLUDE[tsql](../../includes/tsql-md.md)] или другого управляемого кода.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Требования для определяемых пользователем статистических функций CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 Содержит общие сведения о требованиях к реализации определяемых пользователем агрегатных функций среды CLR.  
  
 [Вызов определяемых пользователем агрегатных функций CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 Рассказывает о способах вызова определяемой пользователем статистической функции.  
  
  
