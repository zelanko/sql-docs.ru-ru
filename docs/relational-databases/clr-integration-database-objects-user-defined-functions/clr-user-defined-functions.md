---
title: Определяемые пользователем функции CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
caps.latest.revision: 46
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 78f95d7da1a879c2ef33bed15709541cb399660b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917759"
---
# <a name="clr-user-defined-functions"></a>Определяемые пользователем функции среды CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Определяемые пользователем функции представляют собой подпрограммы, которые могут принимать параметры, выполнять вычисления или другие действия и возвращать результат. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], определяемую пользователем функцию можно написать на любом языке программирования платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, например на [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Существует два типа функций: скалярные, возвращающие одно значение, и табличные, возвращающие набор значений.  
  
 В следующей таблице приводится список подразделов данного раздела.  
  
 [Скалярные функции CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-scalar-valued-functions.md)  
 Приводит сведения о требованиях реализации и примеры скалярных функций.  
  
 [Возвращающие табличные значения функции CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
 Объясняет реализацию и использование функций с табличным значением (TVF), а также разницу между возвращающими табличные значения функциями в [!INCLUDE[tsql](../../includes/tsql-md.md)] и в среде CLR.  
  
 [Определяемые пользователем статистические функции CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)  
 Объясняет реализацию и использование определяемых пользователем статистических функций.  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем функции](../../relational-databases/user-defined-functions/user-defined-functions.md)  
  
  
