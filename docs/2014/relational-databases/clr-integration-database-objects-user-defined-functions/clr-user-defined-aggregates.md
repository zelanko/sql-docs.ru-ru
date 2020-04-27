---
title: Определяемые пользователем статистические функции CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 59666e90a47d88762c6fc3bd1fabc0e71ea18f94
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919581"
---
# <a name="clr-user-defined-aggregates"></a>Пользовательские агрегатные функции среды CLR
  Агрегатные функции выполняют вычисление на наборе значений и возвращают одиночное значение. Традиционно поддерживаются только встроенные агрегатные функции, такие как `SUM` или `MAX`, которые работают с набором входных скалярных значений и создают одно статистическое значение из этого набора. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Но теперь интеграция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со средой [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR позволяет создавать в управляемом коде пользовательские агрегатные функции и предоставлять доступ к ним из [!INCLUDE[tsql](../../includes/tsql-md.md)] или другого управляемого кода.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Требования для определяемых пользователем статистических функций CLR](clr-user-defined-aggregates-requirements.md)  
 Содержит общие сведения о требованиях к реализации определяемых пользователем агрегатных функций среды CLR.  
  
 [Вызов определяемых пользователем агрегатных функций CLR](clr-user-defined-aggregate-invoking-functions.md)  
 Рассказывает о способах вызова определяемой пользователем статистической функции.  
  
  
