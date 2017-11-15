---
title: "Указание фильтра для точек останова | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.breakpt.contraints
helpviewer_keywords: Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 242653e9766535cb5282b3cabdf3850e5b0f96be
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="specify-a-breakpoint-filter"></a>Задание фильтра точек останова
  Фильтр для точек останова ограничивает действие точки останова определенными компьютерами, процессами операционной системы и потоками. Фильтры точек останова обычно используются при отладке параллельных приложений.  
  
##  <a name="BKMK_ActionConsiderations"></a> Вопросы применения фильтров  
 Обычно фильтры точек останова используют вместе с отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] , потому что скрипты и хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] не являются параллельными приложениями.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>Задание фильтра точки останова  
  
1.  В окне редактора щелкните метку точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Фильтр** .  
  
     -или-  
  
     В окне **Точки останова** щелкните метку точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Фильтр** .  
  
2.  В диалоговом окне **Фильтры точки останова** используйте флажок **Фильтр** для указания компьютеров по имени или процессов и потоков операционной системы по имени или идентификационному номеру.  
  
    -   **MachineName** — это компьютер, на котором запущен экземпляр Database Engine.  
  
    -   **ProcessID**и **ProcessName** — это процесс операционной системы, в котором исполняется экземпляр компонента Database Engine.  
  
    -   **ThreadID** и **ThreadName** — это поток операционной системы, в котором выполняется пакет, процедура или функция [!INCLUDE[tsql](../../includes/tsql-md.md)] на экземпляре Database Engine.  
  
3.  Нажмите кнопку **ОК** , чтобы внести изменения, либо кнопку **Отмена** , чтобы выйти без их применения.  
  
## <a name="see-also"></a>См. также:  
 [Задание условия точки останова](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Настройка счетчика числа попаданий](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Задание действия в точке останова](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
