---
title: Работа с Analysis Services проектами и базами данных на этапе разработки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3ab225433ca4ab08d7a7c013fa30dd37c05b9143
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072454"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a>Работа с проектами и базами данных служб Analysis Services на этапе разработки
  База данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может быть разработана в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта или в режиме в сети.  
  
## <a name="single-developer"></a>Один разработчик  
 Если база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и все составляющие ее объекты разрабатываются одним разработчиком, то он может пользоваться средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и в режиме проекта, и в режиме в сети в любое время в течение всего срока жизни решения бизнес-аналитики. В случае одного разработчика выбор режима является не очень важным. Поддержка файла проекта вне сети, встроенного в систему управления версиями, имеет много преимуществ, например возможность архивирования и отката. Однако при одном разработчике отсутствует проблема обмена изменениями с другим разработчиком.  
  
## <a name="multiple-developers"></a>Несколько разработчиков  
 Если над решением бизнес-аналитики работает несколько разработчиков, могут возникнуть проблемы, если разработчики не работают в режиме проекта с системой управления версиями, а порой и в противном случае. Система управления версиями обеспечивает то, что два разработчика одновременно не выполняют изменения одного и того же объекта.  
  
 Пусть, например, разработчик работает в режиме проекта и производит изменения в выбранных объектах. Допустим, что в то время, когда этот разработчик выполняет изменения, другой разработчик вносит изменение в развернутую базу данных в режиме в сети. Возникнет проблема, если первый разработчик попытается развернуть свой измененный проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . То есть среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] обнаружит, что в развернутой базе данных объекты изменены, и предложит разработчику переписать всю базу данных, переписав изменения второго разработчика. Так как в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] нет средств разрешения изменений между экземпляром базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и объектами в проекте, которые должны быть переписаны, единственной реальной возможностью, имеющейся у первого разработчика, является решение отказаться от своих изменений и заново начать новый проект, основанный на текущей версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
  
