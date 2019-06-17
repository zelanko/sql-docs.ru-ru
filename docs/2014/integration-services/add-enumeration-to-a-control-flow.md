---
title: Добавление перечисления к потоку управления | Документация Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cad9c6a3537fb523a13f0206eed6c8eee837ed06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061911"
---
# <a name="add-enumeration-to-a-control-flow"></a>Добавление перечисления к потоку управления
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]включают в себя контейнер "Цикл по каждому элементу" — элемент потока управления, который позволяет легко использовать циклы, перечисляющие файлы и объекты в потоке управления пакета. Дополнительные сведения см. в разделе [Контейнер «цикл по каждому элементу»](control-flow/foreach-loop-container.md).  
  
 Контейнер «цикл по каждому элементу» не добавляет новых функций, он только предоставляет структуру, в которой можно построить повторяемый поток управления, указать тип перечислителя и задать его параметры. Чтобы контейнер заработал, необходимо включить в контейнер «цикл по каждому элементу» как минимум одну задачу. Дополнительные сведения см. в разделе [Integration Services Tasks](control-flow/integration-services-tasks.md).  
  
 Контейнер «цикл по каждому элементу» может включать поток управления из нескольких задач и может содержать другие контейнеры. Добавление задач и контейнеров в контейнер «цикл по каждому элементу» сходно с добавлением их к пакету, только перетаскивание происходит в контейнер «цикл по каждому элементу», а не в пакет. Если контейнер «цикл по каждому элементу» содержит более одной задачи или контейнера, их можно соединить с использованием объектов управления очередностью, как и в пакете. Дополнительные сведения см. в статье [Precedence Constraints](control-flow/precedence-constraints.md).  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a>Включение контейнера «цикл по каждому элементу» в поток управления  
  
1.  Добавьте к пакету контейнер «цикл по каждому элементу». Дополнительные сведения см. в разделе [Добавление или удаление задачи или контейнера в поток управления](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
2.  Добавьте в контейнер «цикл по каждому элементу» задачи и контейнеры. Дополнительные сведения см. в разделе [Добавление или удаление задачи или контейнера в поток управления](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
3.  Соедините задачи и контейнеры в контейнере «цикл по каждому элементу» с помощью объектов управления очередностью. Дополнительные сведения см. в разделе [Соединение задач и контейнеров с помощью элементов управления очередностью по умолчанию](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Задайте параметры контейнера «цикл по каждому элементу». Дополнительные сведения см. в разделе [Настройка контейнера "цикл по каждому элементу"](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление задачи или контейнера в поток управления или удалить их из него](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Группирование и разгруппирование компонентов](group-or-ungroup-components.md)   
 [Управление очередностью](control-flow/precedence-constraints.md)   
 [Добавление итерации к потоку управления](add-iteration-to-a-control-flow.md)   
 [Поток управления](control-flow/control-flow.md)  
  
  
