---
title: Несколько ограничений очередности | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5f06a05ff275151e2488b1f3ec89c8d9cb7afb12
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890738"
---
# <a name="multiple-precedence-constraints"></a>Множественные элементы управления очередностью
  Объект управления очередностью соединяет два исполняемых объекта: две задачи, два контейнера или задачу и контейнер. Они известны как приоритетный исполняемый объект и исполняемый объект с ограничением. Исполняемый объект с ограничениями может иметь несколько элементов управления очередностью. Дополнительные сведения см. в статье [Precedence Constraints](control-flow/precedence-constraints.md).  
  
 Сборка сложных сценариев ограничений путем их группирования позволяет создавать сложный поток управления в пакетах. Например, на следующей иллюстрации задача Г связана с задачей А ограничением `Success`, задача Г с задачей Б — ограничением `Failure`, а задачи Г и В — ограничением `Success`. Элементы управления очередностью между задачами Г и А, между Г и Б, а также между Г и В участвуют в логических связях типа *and* . Таким образом, для запуска задачи Г должна успешно запуститься задача А, аварийно завершиться задача Б и успешно запуститься задача В.  
  
 ![Задачи, связанные с элементами управления очередностью](media/precedenceconstraints.gif "Задачи, связанные с элементами управления очередностью")  
  
## <a name="logicaland-property"></a>Свойство LogicalAnd  
 Если задача или контейнер содержит несколько ограничений, то при помощи свойства `LogicalAnd` указывается, следует ли вычислять управление очередностью отдельно или вместе с остальными ограничениями.  
  
 Можно задать `LogicalAnd` свойства с помощью **редактор управления очередностью** в [!INCLUDE[ssIS](../includes/ssis-md.md)] конструктор, или в окне «Свойства», [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предоставляет.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Установка свойств управления очередностью](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
