---
title: окно локальных переменных
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 70ee1eee120c94e7f851bc37c3becf1983a57d09
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253053"
---
# <a name="transact-sql-debugger---locals-window"></a>Отладчик Transact-SQL, окно локальных переменных

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В окне **Локальные переменные** отображаются сведения о локальных выражениях в текущей области отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] . Областью является текущий кадр стека вызова, выбранный в окне **Стек вызовов** . Чтобы иметь возможность просматривать локальные выражения, необходимо находиться в режиме отладки.  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Список задач

**Доступ к окну «Локальные переменные»**
  
-   В меню **Отладка** выберите пункт **Окна**, а затем пункт **Локальные переменные**.  
  
 **Изменение значения выражения**  
  
-   Щелкните правой кнопкой мыши выражение и выберите команду **Изменить значение**.  
  
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
