---
title: окно просмотра значений
titleSuffix: T-SQL Debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.reviewer: ''
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab0abfe0e2221da335e069ef2f8ba6de38c1d3f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75252992"
---
# <a name="transact-sql-debugger---watch-window"></a>Отладчик Transact-SQL, окно контрольных значений

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В окне **Контрольные значения** отображается информация о выбранных выражениях. Может быть открыто четыре окна контрольных значений: **Контрольные значения 1**, **Контрольные значения 2, Контрольные значения 3**и **Контрольные значения 4**. Выражения вычисляются в области текущего кадра стека вызова, который выбран в окне **Стек вызовов** . Чтобы иметь возможность контролировать значения переменных и выражений, необходимо находиться в режиме отладки.  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Список задач

**Доступ к окнам «Контрольные значения»**  
  
-   В меню **Отладка** выберите пункт **Окна**, затем пункт **Контрольные значения**и выберите пункт **Контрольные значения 1**, **Контрольные значения 2, Контрольные значения 3**или **Контрольные значения 4**.  
  
 **Изменение значения выражения**  
  
-   Щелкните правой кнопкой мыши выражение и выберите команду **Изменить значение**.  
  
## <a name="columns"></a>Столбцы  
 **Название**  
 Выражения, перечисляемые отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] . Поддерживаются следующие выражения:  
  
-   Переменные.  
  
-   Параметры.  
  
-   Системные функции, имена которых начинаются с @@.  
  
-   Выражения, построенные путем применения операторов к одной или нескольким переменным, параметрам или системным функциям, например @IntegerCounter+1 или FirstName+LastName.  
  
-   Инструкции Transact-SQL, возвращающие единственное значение, например SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
 **Value**  
 Отображается значение, возвращаемое после оценки отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] выражения, указанного в поле **Имя**.  
  
 Если длина выражения больше ширины столбца **Значение** , полное значение отображается в подсказке при перемещении указателя на ячейку **Значение** для этого выражения.  
  
 Значок лупы в ячейке **Значение** указывает, что доступен визуализатор отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] . В этом списке можно указать **Визуализатор текста**, **Визуализатор XML**или **Визуализатор HTML**. Чтобы выполнить запуск визуализатора отладчика, щелкните значок лупы. В отладчике [!INCLUDE[tsql](../../includes/tsql-md.md)] откроется диалоговое окно, в котором данные будут отображены в формате, соответствующем типу этих данных.  
  
 **Тип**  
 Отображает тип данных выражения.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Сведения отладчика Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [окно локальных переменных](../../relational-databases/scripting/transact-sql-debugger-locals-window.md)   
 [Окно стека вызовов](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Диалоговое окно «Быстрая проверка»](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)  
