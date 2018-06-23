---
title: Измените приложения, чтобы значения типа bigint из sysperfinfo.cntr_value | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 436e4d7dc8f1e4a98cfab2b0f2ce2c77576950f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098567"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>Измените приложения, чтобы они использовали значения bigint из столбца sysperfinfo.cntr_value
  Возвращает представление sysperfinfo `bigint` значение для столбца cntr_value.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Внесите изменения в приложения, использующие представление sysperfinfo, чтобы убедиться, что они могут обрабатывать значение типа `bigint` столбца cntr_value.  
  
> [!NOTE]  
>  sysperfinfo является представлением совместимости. Вместо него следует использовать динамическое административное представление sys.dm_os_performance_counters.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
