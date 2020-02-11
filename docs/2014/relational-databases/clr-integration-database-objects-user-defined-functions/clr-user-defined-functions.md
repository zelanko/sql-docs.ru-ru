---
title: Определяемые пользователем функции CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f48a62e1dff2fbc1d226077c2271e8a8a71efb2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874489"
---
# <a name="clr-user-defined-functions"></a>Определяемые пользователем функции среды CLR
  Определяемые пользователем функции представляют собой подпрограммы, которые могут принимать параметры, выполнять вычисления или другие действия и возвращать результат. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], определяемую пользователем функцию можно написать на любом языке программирования платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, например на [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Существует два типа функций: скалярные, возвращающие одно значение, и табличные, возвращающие набор значений.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Скалярные функции среды CLR](clr-scalar-valued-functions.md)  
 Приводит сведения о требованиях реализации и примеры скалярных функций.  
  
 [Функции среды CLR с табличным значением](clr-table-valued-functions.md)  
 Объясняет реализацию и использование функций с табличным значением (TVF), а также разницу между возвращающими табличные значения функциями в [!INCLUDE[tsql](../../includes/tsql-md.md)] и в среде CLR.  
  
 [Пользовательские агрегатные функции среды CLR](clr-user-defined-aggregates.md)  
 Объясняет реализацию и использование определяемых пользователем статистических функций.  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем функции](../user-defined-functions/user-defined-functions.md)  
  
  
