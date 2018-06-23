---
title: Определяемые пользователем функции CLR | Документы Microsoft
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
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
caps.latest.revision: 45
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dd7a5d10a15b7072aced0c20b31193e3370488b9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096176"
---
# <a name="clr-user-defined-functions"></a>Определяемые пользователем функции среды CLR
  Определяемые пользователем функции представляют собой подпрограммы, которые могут принимать параметры, выполнять вычисления или другие действия и возвращать результат. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], определяемую пользователем функцию можно написать на любом языке программирования платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, например на [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Существует два типа функций: скалярные, возвращающие одно значение, и табличные, возвращающие набор значений.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Скалярные функции среды CLR](clr-scalar-valued-functions.md)  
 Приводит сведения о требованиях реализации и примеры скалярных функций.  
  
 [Функции среды CLR, возвращающие табличное значение](clr-table-valued-functions.md)  
 Объясняет реализацию и использование функций с табличным значением (TVF), а также разницу между возвращающими табличные значения функциями в [!INCLUDE[tsql](../../includes/tsql-md.md)] и в среде CLR.  
  
 [Определяемые пользователем агрегатные функции среды CLR](clr-user-defined-aggregates.md)  
 Объясняет реализацию и использование определяемых пользователем статистических функций.  
  
## <a name="see-also"></a>См. также  
 [Определяемые пользователем функции](../user-defined-functions/user-defined-functions.md)  
  
  