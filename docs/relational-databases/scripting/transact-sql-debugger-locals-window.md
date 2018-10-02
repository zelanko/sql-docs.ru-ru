---
title: Окно "Локальные переменные" | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.locals
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2285b8a55a1162a49b96c41e1fb81b5e5fc5931f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710312"
---
# <a name="transact-sql-debugger---locals-window"></a>Отладчик Transact-SQL, окно локальных переменных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В окне **Локальные переменные** отображаются сведения о локальных выражениях в текущей области отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] . Областью является текущий кадр стека вызова, выбранный в окне **Стек вызовов** . Чтобы иметь возможность просматривать локальные выражения, необходимо находиться в режиме отладки.  
  
## <a name="task-list"></a>Список задач  
 **Доступ к окну «Локальные переменные»**  
  
-   В меню **Отладка** выберите пункт **Окна**, а затем пункт **Локальные переменные**.  
  
 **Изменение значения выражения**  
  
-   Щелкните правой кнопкой мыши выражение и выберите **Изменить значение**.  
  
## <a name="columns"></a>Столбцы  
 **Название**  
 Имя локального выражения. В отладчике [!INCLUDE[tsql](../../includes/tsql-md.md)] перечисляются переменные, параметры и системные функции, имена которых начинаются с @@.  
  
 **Value**  
 Отображается значение, которое в настоящее время присвоено локальному выражению. Этот столбец остается пустым, если выражению не присвоено значение.  
  
 Если длина выражения больше ширины столбца **Значение** , полное значение отображается в подсказке при перемещении указателя на ячейку **Значение** для этого выражения.  
  
 Значок лупы в ячейке **Значение** указывает, что доступен визуализатор отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] . В этом списке можно указать **Визуализатор текста**, **Визуализатор XML**или **Визуализатор HTML**. Чтобы выполнить запуск визуализатора отладчика, щелкните значок лупы. В отладчике [!INCLUDE[tsql](../../includes/tsql-md.md)] откроется диалоговое окно, в котором данные будут отображены в формате, соответствующем типу этих данных.  
  
 **Тип**  
 Отображает тип данных выражения.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Сведения отладчика Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [окно просмотра значений](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [Окно стека вызовов](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Диалоговое окно «Быстрая проверка»](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
