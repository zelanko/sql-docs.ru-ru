---
title: Просмотр объектов пакета | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 3c8b2f7a7d458d8c34c62768aa8d22fdd8d3e284
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65713924"
---
# <a name="view-package-objects"></a>просмотр объектов пакета

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вкладка **Обозреватель пакетов** предоставляет режим обозревателя. В данном режиме отображается иерархия контейнеров архитектуры [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Контейнер пакетов стоит на самом верху иерархии. При разворачивании пакета можно просмотреть все соединения, исполняемые объекты, обработчики событий, регистраторы, объекты управления очередностью и переменные.  
  
 Исполняемые объекты, то есть контейнеры и задачи в пакете, могут содержать обработчики событий, элементы управления очередностью и переменные. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] поддерживают вложенную иерархию контейнеров, а контейнеры «цикл по элементам», «цикл по каждому элементу» и контейнер последовательности могут содержать другие исполняемые объекты.  
  
 Если пакет содержит поток данных, то вкладка **Обозреватель пакетов** содержит задачу потока данных, а также папку **Компоненты** , которая содержит список компонентов потока данных.  
  
 На вкладке **Обозреватель пакетов** можно удалять объекты из пакета, а также открыть окно **Свойства** для просмотра свойств объектов.  
  
 На следующей диаграмме показана древовидная структура простого пакета.  
  
 ![Снимок экрана: вкладка "Обозреватель пакетов"](../integration-services/media/packageexplorer.gif "Снимок экрана: вкладка \"Обозреватель пакетов\"")  
  
## <a name="view-the-package-structure-and-content"></a>Просмотр структуры и содержимого пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с пакетом, который необходимо просмотреть в **обозревателе пакетов**.  
  
2.  Перейдите на вкладку **Обозреватель пакетов** .  
  
3.  Чтобы просмотреть содержимое папок **Переменные**, **Управление очередностью**, **Обработчики события**, **Диспетчеры соединений**, **Регистраторы**или **Исполняемые объекты** , раскройте соответствующую папку.  
  
4.  В зависимости от структуры пакета раскройте папки следующих уровней.  
  
## <a name="view-the-properties-of-a-package-object"></a>Просмотр свойств объекта пакета
  
-   Щелкните объект правой кнопкой мыши и выберите пункт **Свойства** , чтобы открыть окно **Свойства** .  
  
## <a name="delete-an-object-in-a-package"></a>Удаление объекта в пакете  
  
-   Щелкните объект правой кнопкой мыши и выберите пункт **Удалить**. 
 
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../integration-services/control-flow/integration-services-tasks.md)   
 [Контейнеры служб Integration Services](../integration-services/control-flow/integration-services-containers.md)   
 [Управление очередностью](../integration-services/control-flow/precedence-constraints.md)   
 [Переменные в службах Integration Services (SSIS)](../integration-services/integration-services-ssis-variables.md)   
 [Обработчики событий в службах Integration Services (SSIS)](../integration-services/integration-services-ssis-event-handlers.md)   
 [Ведение журналов в службах Integration Services (SSIS)](../integration-services/performance/integration-services-ssis-logging.md)  
  
  
