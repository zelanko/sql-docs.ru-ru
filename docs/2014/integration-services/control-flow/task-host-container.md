---
title: Контейнер "Сервер задач" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 377ec6b276d2cc83b296a9d0676f39bc9039ca80
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165244"
---
# <a name="task-host-container"></a>контейнер «Сервер задач»
  Контейнер «Сервер задач» содержит одну задачу. В конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] сервер задач не настраивается отдельно; он настраивается при определении свойств содержащейся в нем задачи. Дополнительные сведения о задачах, которые содержат контейнеры узла задач см. в разделе [Integration Services Tasks](integration-services-tasks.md).  
  
 Этот контейнер расширяет применение переменных и обработчиков событий до уровня задач. Дополнительные сведения см. в разделах [Обработчики событий в службах Integration Services (SSIS)](../integration-services-ssis-event-handlers.md) и [Переменные в службах Integration Services (SSIS)](../integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Настройка сервера задач  
 Задать свойства можно в окне **Свойства** среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программными средствами.  
  
 Дополнительные сведения о настройке свойств этих свойств в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]см. в разделе [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md).  
  
 Дополнительные сведения о настройке этих свойств программными средствами см. в разделе <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>См. также  
 [Контейнеры служб Integration Services](integration-services-containers.md)  
  
  
