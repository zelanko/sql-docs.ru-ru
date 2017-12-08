---
title: "Работа с проектами и разработки баз данных служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 26ffb60b07dad8af5d76304b7b58359e11bee8b7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>Работа с проектами и разработки баз данных служб Analysis Services
  База данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может быть разработана в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта или в режиме в сети.  
  
## <a name="single-developer"></a>Один разработчик  
 Если база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и все составляющие ее объекты разрабатываются одним разработчиком, то он может пользоваться средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и в режиме проекта, и в режиме в сети в любое время в течение всего срока жизни решения бизнес-аналитики. В случае одного разработчика выбор режима является не очень важным. Поддержка файла проекта вне сети, встроенного в систему управления версиями, имеет много преимуществ, например возможность архивирования и отката. Однако при одном разработчике отсутствует проблема обмена изменениями с другим разработчиком.  
  
## <a name="multiple-developers"></a>Несколько разработчиков  
 Если над решением бизнес-аналитики работает несколько разработчиков, могут возникнуть проблемы, если разработчики не работают в режиме проекта с системой управления версиями, а порой и в противном случае. Система управления версиями обеспечивает то, что два разработчика одновременно не выполняют изменения одного и того же объекта.  
  
 Пусть, например, разработчик работает в режиме проекта и производит изменения в выбранных объектах. Допустим, что в то время, когда этот разработчик выполняет изменения, другой разработчик вносит изменение в развернутую базу данных в режиме в сети. Возникнет проблема, если первый разработчик попытается развернуть свой измененный проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . То есть среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] обнаружит, что в развернутой базе данных объекты изменены, и предложит разработчику переписать всю базу данных, переписав изменения второго разработчика. Так как в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] нет средств разрешения изменений между экземпляром базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и объектами в проекте, которые должны быть переписаны, единственной реальной возможностью, имеющейся у первого разработчика, является решение отказаться от своих изменений и заново начать новый проект, основанный на текущей версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
  
