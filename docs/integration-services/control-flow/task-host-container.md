---
title: Контейнер "Сервер задач" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 75a01f8321dcd70b0e3f08c36dfaf04b5e86bd8c
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727416"
---
# <a name="task-host-container"></a>контейнер «Сервер задач»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Контейнер «Сервер задач» содержит одну задачу. В конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] сервер задач не настраивается отдельно; он настраивается при определении свойств содержащейся в нем задачи. Дополнительные сведения о задачах, которые содержат контейнеры узла задач см. в разделе [Integration Services Tasks](../../integration-services/control-flow/integration-services-tasks.md).  
  
 Этот контейнер расширяет применение переменных и обработчиков событий до уровня задач. Дополнительные сведения см. в разделах [Обработчики событий в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-event-handlers.md) и [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Настройка сервера задач  
 Задать свойства можно в окне **Свойства** среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программными средствами.  
  
 Дополнительные сведения о настройке свойств этих свойств в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]см. в разделе [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
 Дополнительные сведения о настройке этих свойств программными средствами см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>См. также:  
 [Контейнеры служб Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  
