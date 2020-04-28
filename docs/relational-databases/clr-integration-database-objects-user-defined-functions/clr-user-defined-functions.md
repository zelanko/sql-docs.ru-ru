---
title: Определяемые пользователем функции CLR | Документация Майкрософт
description: SQL Server интеграция со средой CLR позволяет создавать определяемые пользователем скалярные, табличные и агрегатные функции на любом языке программирования .NET Framework.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: 0da524de3a21a97daf6e3b2d2e0277631a4467c0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488287"
---
# <a name="clr-user-defined-functions"></a>Определяемые пользователем функции среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Определяемые пользователем функции представляют собой подпрограммы, которые могут принимать параметры, выполнять вычисления или другие действия и возвращать результат. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], определяемую пользователем функцию можно написать на любом языке программирования платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, например на [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Существует два типа функций: скалярные, возвращающие одно значение, и табличные, возвращающие набор значений.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Скалярные функции среды CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-scalar-valued-functions.md)  
 Приводит сведения о требованиях реализации и примеры скалярных функций.  
  
 [Функции среды CLR с табличным значением](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
 Объясняет реализацию и использование функций с табличным значением (TVF), а также разницу между возвращающими табличные значения функциями в [!INCLUDE[tsql](../../includes/tsql-md.md)] и в среде CLR.  
  
 [Пользовательские агрегатные функции среды CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)  
 Объясняет реализацию и использование определяемых пользователем статистических функций.  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем функции](../../relational-databases/user-defined-functions/user-defined-functions.md)  
  
  
