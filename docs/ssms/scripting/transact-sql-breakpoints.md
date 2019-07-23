---
title: Точки останова Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a2b5e9d6e47a71f8bc65d71e0fb6364e352e8045
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263230"
---
# <a name="transact-sql-breakpoints"></a>Точки останова Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Точка останова указывает, что отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] приостанавливает выполнение на конкретной инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , после чего можно просмотреть состояние элементов кода на данном этапе.  
  
## <a name="breakpoints"></a>Точки останова  
 Когда работает отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] , можно переключать точки останова на определенных инструкциях. Когда выполнение доходит до определенной точки останова, отладчик приостанавливает работу, чтобы вы могли просмотреть такие сведения по отладке, как значения переменных и параметров.  
  
 Этими точками останова можно управлять индивидуально в окне редактора или всеми вместе в окне **Точки останова** . Точки останова можно изменить — например, указать условия, при которых должно приостанавливаться выполнение, или действия, которые должны выполняться, если выполняется точка останова.  
  
## <a name="breakpoint-tasks"></a>Задачи точки останова  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описано, как задать инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] , на которой должен остановиться отладчик.|[Переключение точки останова](../../relational-databases/scripting/toggle-a-breakpoint.md)|  
|Описано, как временно отключить точку останова, а позже снова ее активировать. Описано удаление точку останова.|[Включение, отключение и удаление точек останова](../../relational-databases/scripting/enable-disable-and-delete-breakpoints.md)|  
|Описано, как задать условие срабатывания точки останова в зависимости от результата вычисления указанного выражения Transact-SQL.|[Задание условия точки останова](../../relational-databases/scripting/specify-a-breakpoint-condition.md)|  
|Описано, как задать счетчик попаданий, чтобы точка останова срабатывала только после того, как инструкция с точкой останова была выполнена указанное число раз.|[Настройка счетчика числа попаданий](../../relational-databases/scripting/specify-a-hit-count.md)|  
|Описано, как задать фильтр, по которому точка останова будет срабатывать только для указанных процессов или потоков.|[Задание фильтра точек останова](../../relational-databases/scripting/specify-a-breakpoint-filter.md)|  
|Описано, как задать действие **При попадании** , т. е. пользовательскую операцию, которая выполняется при выполнении инструкции с точкой останова. Например, печать сообщения.|[Задание действия в точке останова](../../relational-databases/scripting/specify-a-breakpoint-action.md)|  
|Описано, как изменить местоположение точки останова.|[Изменение положения точки останова](../../relational-databases/scripting/edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a>См. также:  
 [Сведения отладчика Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)  
  
  
