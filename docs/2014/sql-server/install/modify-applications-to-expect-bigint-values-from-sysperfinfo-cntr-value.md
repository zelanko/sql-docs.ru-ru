---
title: Изменение приложений для ожидания значений bigint из sysperfinfo. cntr_value | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012207"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a>Измените приложения, чтобы они использовали значения bigint из столбца sysperfinfo.cntr_value
  sysperfinfo возвращает `bigint` значение для столбца cntr_value.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Внесите изменения в приложения, использующие представление sysperfinfo, чтобы убедиться, что они могут обрабатывать значение типа `bigint` столбца cntr_value.  
  
> [!NOTE]  
>  sysperfinfo является представлением совместимости. Вместо него следует использовать динамическое административное представление sys.dm_os_performance_counters.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
