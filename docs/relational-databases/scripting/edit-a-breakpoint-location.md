---
title: "Измерение положения точки останова | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpt.location.file
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17e1810114e209c8012792b1e67502c3638afa3a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="edit-a-breakpoint-location"></a>Изменение положения точки останова
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Положение точки останова задает строку и символ, где находится точка останова в файле скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)]. Положение точки останова можно изменить и перенести точку останова в другое место в скрипте или в другой скрипт.  
  
## <a name="editing-a-location"></a>Изменение положения  
 При изменении положения точки останова она перемещается в новое место вместе со всеми существующими свойствами, такими как число попаданий или условие.  
  
#### <a name="to-edit-a-breakpoint-location"></a>Изменение положения точки останова  
  
1.  В окне редактора щелкните метку точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Положение** .  
  
     -или-  
  
     В окне **Точки останова** щелкните метку точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Положение** .  
  
2.  В диалоговом окне **Точка останова в файле** в поле **Файл** укажите новый файл, в поле **Строка** укажите новую строку, а в поле **Символ** укажите новое расположение в строке. Если новый указанный файл уже открыт в окне редактора запросов, точка останова перемещается в это окно редактора. Если файл не открыт, открывается новое окно редактора, в него загружается указанный файл и точка останова перемещается в новое расположение.  
  
     При отладке **параметр** Разрешить наличие отличий в исходном коде от первоначальной версии [!INCLUDE[tsql](../../includes/tsql-md.md)]не учитывается.  
  
## <a name="see-also"></a>См. также:  
 [Настройка счетчика числа попаданий](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Задание действия в точке останова](../../relational-databases/scripting/specify-a-breakpoint-action.md)   
 [Задание условия точки останова](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Задание фильтра точек останова](../../relational-databases/scripting/specify-a-breakpoint-filter.md)  
  
  
