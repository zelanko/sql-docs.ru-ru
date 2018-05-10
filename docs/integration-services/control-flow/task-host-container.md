---
title: Контейнер "Сервер задач" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 706f68e58888675ca057ebc6bcf95bfdc52884eb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="task-host-container"></a>контейнер «Сервер задач»
  Контейнер «Сервер задач» содержит одну задачу. В конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] сервер задач не настраивается отдельно; он настраивается при определении свойств содержащейся в нем задачи. Дополнительные сведения о задачах, которые содержат контейнеры узла задач см. в разделе [Integration Services Tasks](../../integration-services/control-flow/integration-services-tasks.md).  
  
 Этот контейнер расширяет применение переменных и обработчиков событий до уровня задач. Дополнительные сведения см. в разделах [Обработчики событий в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-event-handlers.md) и [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Настройка сервера задач  
 Задать свойства можно в окне **Свойства** среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программными средствами.  
  
 Дополнительные сведения о настройке свойств этих свойств в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]см. в разделе [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
 Дополнительные сведения о настройке этих свойств программными средствами см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>См. также:  
 [Контейнеры служб Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  
