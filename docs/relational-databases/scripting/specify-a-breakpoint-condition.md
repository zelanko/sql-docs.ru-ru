---
title: "Указание условия в точке останова | Документация Майкрософт"
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
- vs.debug.breakpt.condition
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 258075ed4da79b1c53eb73836d62e873025ea0be
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="specify-a-breakpoint-condition"></a>Задание условия точки останова
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Условие точки останова — это выражение [!INCLUDE[tsql](../../includes/tsql-md.md)], проверяемое отладчиком по достижении точки останова. Если достигнуто указанное число попаданий или удовлетворяется указанное условие, то отладчик останавливает выполнение или выполняет действие, заданное для точки останова.  
  
## <a name="specifying-conditions"></a>Задание условий  
 Необходимо задать допустимое выражение Transact-SQL, результатом вычисления которого является логическое значение. Дополнительные сведения см. в разделе [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 Если задать условие точки останова с недопустимым синтаксисом, немедленно появится предупреждение. Если задать условие с допустимым синтаксисом, но недопустимой семантикой, предупреждение появится, когда точка останова будет достигнута в первый раз. В любом случае отладчик прервет выполнение, как только будет достигнута недопустимая точка останова.  
  
#### <a name="to-specify-a-condition"></a>Задание условия  
  
1.  В окне редактора щелкните глиф точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Условие** .  
  
     -или-  
  
     В окне **Точки останова** щелкните глиф точки останова правой кнопкой мыши и выберите в контекстном меню пункт **Условие** .  
  
2.  Введите в поле **Условие** диалогового окна **Условие точки останова** допустимое логическое выражение.  
  
3.  Если выбрать **Истинно** , выполнение будет прерываться, когда выражение принимает значение **true**, а если **Изменилось** — когда значения выражения изменяется.  
  
    > [!NOTE]  
    >  Отладчик не проверяет это логическое выражение, пока не будет достигнута первая точка останова. Если выбрать **Изменилось**, отладчик не будет считать первую проверку изменением и, следовательно, не будет прерывать при ней исполнение.  
  
## <a name="see-also"></a>См. также:  
 [Настройка счетчика числа попаданий](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Задание действия в точке останова](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
