---
title: Просмотр объектов пакета | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 78a9b551ae44348de1c007533be3606b33c974cd
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390092"
---
# <a name="view-package-objects"></a>просмотр объектов пакета
  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вкладка **Обозреватель пакетов** предоставляет режим обозревателя. В данном режиме отображается иерархия контейнеров архитектуры [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Контейнер пакетов стоит на самом верху иерархии. При разворачивании пакета можно просмотреть все соединения, исполняемые объекты, обработчики событий, регистраторы, объекты управления очередностью и переменные.  
  
 Исполняемые объекты, то есть контейнеры и задачи в пакете, могут содержать обработчики событий, элементы управления очередностью и переменные. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] поддерживают вложенную иерархию контейнеров, а контейнеры «цикл по элементам», «цикл по каждому элементу» и контейнер последовательности могут содержать другие исполняемые объекты.  
  
 Если пакет содержит поток данных, то вкладка **Обозреватель пакетов** содержит задачу потока данных, а также папку **Компоненты** , которая содержит список компонентов потока данных.  
  
 На вкладке **Обозреватель пакетов** можно удалять объекты из пакета, а также открыть окно **Свойства** для просмотра свойств объектов.  
  
 На следующей диаграмме показана древовидная структура простого пакета.  
  
 ![Снимок экрана: вкладка "Обозреватель пакетов"](media/packageexplorer.gif "Снимок экрана: вкладка \"Обозреватель пакетов\"")  
  
### <a name="to-view-package-content"></a>Просмотр содержимого пакета  
  
-   [Просмотр объектов пакета в обозревателе пакетов](../../2014/integration-services/view-package-objects-in-package-explorer.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](control-flow/integration-services-tasks.md)   
 [Контейнеры служб Integration Services](control-flow/integration-services-containers.md)   
 [Управление очередностью](control-flow/precedence-constraints.md)   
 [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md)   
 [Обработчики событий в службах Integration Services (SSIS)](integration-services-ssis-event-handlers.md)   
 [Ведение журналов в службах Integration Services (SSIS)](performance/integration-services-ssis-logging.md)  
  
  
