---
title: Определяемые пользователем статистические функции CLR | Документы Microsoft
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
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dd22a27772c7bcad2d3c98027dbc91d6d6859509
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096178"
---
# <a name="clr-user-defined-aggregates"></a>Пользовательские агрегатные функции среды CLR
  Агрегатные функции выполняют вычисление на наборе значений и возвращают одиночное значение. В большинстве случаев [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживала только встроенные агрегатные функции, такие как `SUM` или `MAX`, что работать с набором входных скалярных величин и создания единственное статистическое значение из этого набора. Но теперь интеграция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со средой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR позволяет создавать в управляемом коде пользовательские агрегатные функции и предоставлять доступ к ним из [!INCLUDE[tsql](../../includes/tsql-md.md)] или другого управляемого кода.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Требования для определяемых пользователем статистических функций CLR](clr-user-defined-aggregates-requirements.md)  
 Содержит общие сведения о требованиях к реализации определяемых пользователем агрегатных функций среды CLR.  
  
 [Вызов определяемых пользователем агрегатных функций CLR](clr-user-defined-aggregate-invoking-functions.md)  
 Рассказывает о способах вызова определяемой пользователем статистической функции.  
  
  