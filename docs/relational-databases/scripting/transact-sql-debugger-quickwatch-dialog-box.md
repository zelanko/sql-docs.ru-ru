---
title: Диалоговое окно "Быстрая проверка" | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 85947c35a9c58726d7f65a2d166f060845205d3f
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="transact-sql-debugger---quickwatch-dialog-box"></a>Отладчик Transact-SQL, диалоговое окно "Быстрая проверка"
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Используйте диалоговое окно **Быстрая проверка** , чтобы быстро просмотреть тип данных и значение одного из выражений [!INCLUDE[tsql](../../includes/tsql-md.md)] , такого как переменная или параметр, при отладке кода [!INCLUDE[tsql](../../includes/tsql-md.md)] . Чтобы просмотреть несколько выражений, можно также добавить выражение в окне **Контрольные значения** .  
  
## <a name="task-list"></a>Список задач  
 **Доступ к диалоговому окну «Быстрая проверка»**  
  
-   В меню **Отладка** выберите пункт **Быстрая проверка**.  
  
 **Просмотр информации о выражении**  
  
1.  В списке **Выражение** введите или выберите необходимое выражение. Поддерживаются следующие выражения [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    -   Переменные.  
  
    -   Параметры.  
  
    -   Системные функции, имена которых начинаются с @@.  
  
    -   Выражения, построенные путем применения операторов к одной или нескольким переменным, параметрам или системным функциям, например @IntegerCounter+1 или FirstName+LastName.  
  
    -   Инструкции Transact-SQL, возвращающие единственное значение, например SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
2.  Нажмите кнопку **Пересчет**.  
  
 **Добавление выражения быстрого просмотра в окно «Просмотр значений»**  
  
-   Нажмите кнопку **Добавить контрольное значение**.  
  
 **Изменение значения выражения быстрой проверки**  
  
-   Щелкните правой кнопкой мыши выражение и выберите команду **Изменить значение**.  
  
## <a name="options"></a>Параметры  
 **Список выражений**  
 Отображается выражение, выбранное в настоящее время. Раскрывающийся список содержит набор выражений, которые можно выбрать для отображения. В списке содержатся выражения, доступные в пределах кадра стека, выбранного в настоящее время в окне **Стек вызова** . Чтобы отобразить другое выражение, введите выражение или выберите его из списка. Отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] поддерживает следующие выражения: переменные, параметры и системные функции, которые имеют имена, начинающиеся с @@.  
  
 **Сетка значений**  
 Отображаются свойства выражения, которое просматривается в настоящее время.  
  
 **Название**  
 Является просматриваемым выражением [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **Value**  
 Отображается значение, которое в настоящее время присвоено выражению. Если в настоящее время выражение не имеет значения, отображается пустое поле.  
  
 Если длина выражения больше ширины столбца **Значение** , полное значение отображается в подсказке при перемещении указателя на ячейку **Значение** для этого выражения.  
  
 Значок лупы в ячейке **Значение** указывает, что доступен визуализатор отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] . В этом списке можно указать **Визуализатор текста**, **Визуализатор XML**или **Визуализатор HTML**. Чтобы выполнить запуск визуализатора отладчика, щелкните значок лупы. В отладчике [!INCLUDE[tsql](../../includes/tsql-md.md)] откроется диалоговое окно, в котором данные будут отображены в формате, соответствующем типу этих данных.  
  
 **Тип**  
 Отображает тип данных выражения.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Сведения отладчика Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [окно просмотра значений](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [окно локальных переменных](../../relational-databases/scripting/transact-sql-debugger-locals-window.md)   
 [Окно стека вызовов](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
