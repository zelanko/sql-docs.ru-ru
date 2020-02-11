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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62926288"
---
# <a name="view-package-objects"></a>просмотр объектов пакета
  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вкладка **Обозреватель пакетов** предоставляет режим обозревателя. В данном режиме отображается иерархия контейнеров архитектуры [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Контейнер пакетов стоит на самом верху иерархии. При разворачивании пакета можно просмотреть все соединения, исполняемые объекты, обработчики событий, регистраторы, объекты управления очередностью и переменные.  
  
 Исполняемые объекты, то есть контейнеры и задачи в пакете, могут содержать обработчики событий, элементы управления очередностью и переменные. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]поддерживает вложенную иерархию контейнеров, а контейнеры «цикл по элементам», «цикл по каждому элементу» и контейнеров последовательности могут включать другие исполняемые объекты.  
  
 Если пакет содержит поток данных, то вкладка **Обозреватель пакетов** содержит задачу потока данных, а также папку **Компоненты** , которая содержит список компонентов потока данных.  
  
 На вкладке **Обозреватель пакетов** можно удалять объекты из пакета, а также открыть окно **Свойства** для просмотра свойств объектов.  
  
 На следующей диаграмме показана древовидная структура простого пакета.  
  
 ![Снимок экрана: вкладка «Обозреватель пакетов»](media/packageexplorer.gif "Снимок экрана: вкладка «Обозреватель пакетов»")  
  
### <a name="to-view-package-content"></a>Просмотр содержимого пакета  
  
-   [Просмотр объектов пакета в обозревателе пакетов](../../2014/integration-services/view-package-objects-in-package-explorer.md)  
  
## <a name="see-also"></a>См. также:  
 [Задачи Integration Services](control-flow/integration-services-tasks.md)   
 [Контейнеры Integration Services](control-flow/integration-services-containers.md)   
 [Управление очередностью](control-flow/precedence-constraints.md)   
 [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md)   
 [Integration Services &#40;служб SSIS&#41; обработчики событий](integration-services-ssis-event-handlers.md)   
 [Ведение журнала&#41; Integration Services &#40;SSIS](performance/integration-services-ssis-logging.md)  
  
  
