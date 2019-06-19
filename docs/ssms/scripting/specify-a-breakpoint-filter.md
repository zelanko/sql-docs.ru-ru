---
title: Указание фильтра для точек останова | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cebd77c1728cc7758e0a4b2077ac0a651bf77f96
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821937"
---
# <a name="specify-a-breakpoint-filter"></a>Задание фильтра точек останова
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
