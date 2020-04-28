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
ms.openlocfilehash: ec6d819d48ba5307e4c5c9e61ef8f7c375d6d96c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176093"
---
# <a name="view-package-objects"></a>просмотр объектов пакета
  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вкладка **Обозреватель пакетов** предоставляет режим обозревателя. В данном режиме отображается иерархия контейнеров архитектуры [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Контейнер пакетов стоит на самом верху иерархии. При разворачивании пакета можно просмотреть все соединения, исполняемые объекты, обработчики событий, регистраторы, объекты управления очередностью и переменные.

 Исполняемые объекты, то есть контейнеры и задачи в пакете, могут содержать обработчики событий, элементы управления очередностью и переменные. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] поддерживают вложенную иерархию контейнеров, а контейнеры «цикл по элементам», «цикл по каждому элементу» и контейнер последовательности могут содержать другие исполняемые объекты.

 Если пакет содержит поток данных, то вкладка **Обозреватель пакетов** содержит задачу потока данных, а также папку **Компоненты** , которая содержит список компонентов потока данных.

 На вкладке **Обозреватель пакетов** можно удалять объекты из пакета, а также открыть окно **Свойства** для просмотра свойств объектов.

 На следующей диаграмме показана древовидная структура простого пакета.

 ![Снимок экрана: вкладка "Обозреватель пакетов"](media/packageexplorer.gif "Снимок экрана: вкладка "Обозреватель пакетов"")

### <a name="to-view-package-content"></a>Просмотр содержимого пакета

-   [Просмотр объектов пакета в обозревателе пакетов](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a>См. также:
 [Integration Services задачи](control-flow/integration-services-tasks.md) [Integration Services](control-flow/integration-services-containers.md) управление [очередностью](control-flow/precedence-constraints.md) контейнеров [Integration Services &#40;SSIS&#41; переменные](integration-services-ssis-variables.md) [Integration Services &#40;службы](integration-services-ssis-event-handlers.md) SSIS&#41; [Журнал](performance/integration-services-ssis-logging.md) Integration Services


