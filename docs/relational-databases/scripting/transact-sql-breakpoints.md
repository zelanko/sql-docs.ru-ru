---
title: "Точки останова Transact-SQL | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f45a852838d3e54f994a55b29e3dcf64eaab8240
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="transact-sql-breakpoints"></a>Точки останова Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Точка останова указывает, что отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] приостанавливает выполнение на конкретной инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], после чего можно просмотреть состояние элементов кода на данном этапе.  
  
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
  
  
