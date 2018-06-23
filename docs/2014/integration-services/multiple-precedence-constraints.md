---
title: Несколько ограничений очередности | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d4a9dc0f4b40320533828e2b1ef9f5f4cdfab9c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101784"
---
# <a name="multiple-precedence-constraints"></a>Множественные элементы управления очередностью
  Объект управления очередностью соединяет два исполняемых объекта: две задачи, два контейнера или задачу и контейнер. Они известны как приоритетный исполняемый объект и исполняемый объект с ограничением. Исполняемый объект с ограничениями может иметь несколько элементов управления очередностью. Дополнительные сведения см. в статье [Precedence Constraints](control-flow/precedence-constraints.md).  
  
 Сборка сложных сценариев ограничений путем их группирования позволяет создавать сложный поток управления в пакетах. Например, на следующей иллюстрации задача Г связана с задачей А `Success` ограничение, задача Г связана с задачей Б `Failure` ограничение, а задачи Г связана задача C, `Success` ограничения. Элементы управления очередностью между задачами Г и А, между Г и Б, а также между Г и В участвуют в логических связях типа *and* . Таким образом, для запуска задачи Г должна успешно запуститься задача А, аварийно завершиться задача Б и успешно запуститься задача В.  
  
 ![Задачи, связанные с элементами управления очередностью](media/precedenceconstraints.gif "Задачи, связанные с элементами управления очередностью")  
  
## <a name="logicaland-property"></a>Свойство LogicalAnd  
 Если задача или контейнер содержит несколько ограничений, то при помощи свойства `LogicalAnd` указывается, следует ли вычислять управление очередностью отдельно или вместе с остальными ограничениями.  
  
 Можно задать `LogicalAnd` свойства с помощью **Редактор ограничений очередностью** в [!INCLUDE[ssIS](../includes/ssis-md.md)] конструкторе или в окне «Свойства», [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предоставляет.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Установка свойств управления очередностью](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  