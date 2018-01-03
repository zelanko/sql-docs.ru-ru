---
title: "Повторное использование объектов пакета | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5de6f3b74a32acf23a042b042fbb1591fd3c3773
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="reuse-of-package-objects"></a>Повторное использование объектов пакета
  Функциональные возможности пакетов, которые требуется использовать повторно. Например, создан набор задач, и необходимо повторно совместно использовать элементы как группу, или необходимо повторно использовать отдельный элемент, такой как диспетчер соединений, созданный в другом проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="copy-and-paste"></a>Копирование и вставка  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и конструктор служб [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer support copying и конструктор служб pasting package objects, which can include control flow items, data flow items, и конструктор служб connection managers. Можно выполнять копирование и вставку между проектами и пакетами. Если в решении содержится несколько проектов, можно выполнять копирование между проектами, и проекты могут принадлежать разным типам.  
  
 Если решение содержит несколько пакетов, можно выполнять копирование и вставку между ними. Пакеты могут находиться в одном или разных проектах служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Однако объекты пакета могут иметь зависимости от других объектов, без которых они недействительны. Например, задача «Выполнение SQL» использует диспетчер соединений, который также необходимо скопировать, чтобы задача работала. Также некоторые объекты пакета требуют, чтобы пакет уже содержал определенный объект, а при отсутствии этого объекта успешная вставка скопированных объектов в пакет невозможна. Например, невозможно вставить поток данных в пакет, если он не содержит хотя бы одну задачу потока данных.  
  
 Может оказаться, что одни и те же пакеты копируются повторно. Чтобы избежать процесса копирования, можно обозначить эти пакеты как шаблоны и использовать их при создании пакетов.  
  
 При копировании объекта пакета службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] автоматически присваивают новый идентификатор GUID свойству **ID** нового объекта и обновляют свойство **Name** .  
  
 Переменные копировать нельзя. Если объект, такой как задача, использует переменные, необходимо повторно создать переменные в целевом пакете. И напротив, при копировании всего пакета переменные пакета также копируются.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Копирование объектов пакета](../integration-services/copy-package-objects.md)  
  
-   [Копирование элементов проекта](http://msdn.microsoft.com/library/1606c54d-20f9-49f3-a4ef-caad83a772aa)  
  
-   [Сохранение пакета в качестве шаблона пакета](http://msdn.microsoft.com/library/efe66cec-3933-4f6e-8d35-fe3d300de66c)  
  
  
