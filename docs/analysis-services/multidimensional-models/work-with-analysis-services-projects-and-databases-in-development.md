---
title: "Работа с проектами и разработки баз данных служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: e68023a30e23c1a34d6dab36d9cbc7265a73469f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>Работа с проектами и разработки баз данных служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Можно разработать [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с помощью [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта или в оперативном режиме.  
  
## <a name="single-developer"></a>Один разработчик  
 Если база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и все составляющие ее объекты разрабатываются одним разработчиком, то он может пользоваться средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и в режиме проекта, и в режиме в сети в любое время в течение всего срока жизни решения бизнес-аналитики. В случае одного разработчика выбор режима является не очень важным. Поддержка файла проекта вне сети, встроенного в систему управления версиями, имеет много преимуществ, например возможность архивирования и отката. Однако при одном разработчике отсутствует проблема обмена изменениями с другим разработчиком.  
  
## <a name="multiple-developers"></a>Несколько разработчиков  
 Если над решением бизнес-аналитики работает несколько разработчиков, могут возникнуть проблемы, если разработчики не работают в режиме проекта с системой управления версиями, а порой и в противном случае. Система управления версиями обеспечивает то, что два разработчика одновременно не выполняют изменения одного и того же объекта.  
  
 Пусть, например, разработчик работает в режиме проекта и производит изменения в выбранных объектах. Допустим, что в то время, когда этот разработчик выполняет изменения, другой разработчик вносит изменение в развернутую базу данных в режиме в сети. Возникнет проблема, если первый разработчик попытается развернуть свой измененный проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . То есть среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] обнаружит, что в развернутой базе данных объекты изменены, и предложит разработчику переписать всю базу данных, переписав изменения второго разработчика. Так как в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] нет средств разрешения изменений между экземпляром базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и объектами в проекте, которые должны быть переписаны, единственной реальной возможностью, имеющейся у первого разработчика, является решение отказаться от своих изменений и заново начать новый проект, основанный на текущей версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
  
