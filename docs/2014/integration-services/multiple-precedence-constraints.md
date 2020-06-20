---
title: Несколько ограничений очередностью | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 61939b09b4a4365c09089df2b52026e96f9427ee
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965154"
---
# <a name="multiple-precedence-constraints"></a>Множественные элементы управления очередностью
  Объект управления очередностью соединяет два исполняемых объекта: две задачи, два контейнера или задачу и контейнер. Они известны как приоритетный исполняемый объект и исполняемый объект с ограничением. Исполняемый объект с ограничениями может иметь несколько элементов управления очередностью. Дополнительные сведения см. в статье [Precedence Constraints](control-flow/precedence-constraints.md).  
  
 Сборка сложных сценариев ограничений путем их группирования позволяет создавать сложный поток управления в пакетах. Например, на следующей иллюстрации задача Г связана с задачей А ограничением `Success`, задача Г с задачей Б — ограничением `Failure`, а задачи Г и В — ограничением `Success`. Элементы управления очередностью между задачами Г и А, между Г и Б, а также между Г и В участвуют в логических связях типа *and* . Таким образом, для запуска задачи Г должна успешно запуститься задача А, аварийно завершиться задача Б и успешно запуститься задача В.  
  
 ![Задачи, связанные ограничениями очередностью](media/precedenceconstraints.gif "Задачи, связанные ограничениями очередностью")  
  
## <a name="logicaland-property"></a>Свойство LogicalAnd  
 Если задача или контейнер содержит несколько ограничений, то при помощи свойства `LogicalAnd` указывается, следует ли вычислять управление очередностью отдельно или вместе с остальными ограничениями.  
  
 Свойство можно задать `LogicalAnd` с помощью редактора управления **очередностью** в [!INCLUDE[ssIS](../includes/ssis-md.md)] конструкторе или в окно свойств, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предоставляемой.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Установка свойств управления очередностью](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
