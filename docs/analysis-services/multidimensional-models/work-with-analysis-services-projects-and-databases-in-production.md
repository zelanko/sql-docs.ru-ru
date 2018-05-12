---
title: Работа с проектами и базами данных в рабочей среде служб Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f90af41c397da20fb26c73bebc6723b9a3cf6270
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="work-with-analysis-services-projects-and-databases-in-production"></a>Работа с проектами и базами данных в рабочей среде служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  После разработки и развертывания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , необходимо предложить способ выполнения изменений объектов в развернутой базе данных. Некоторые изменения, например связанные с ролями безопасности, секционированием и настройкой хранилищ, можно выполнить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Другие изменения (например, добавление атрибутов и пользовательских иерархий) могут быть выполнены только в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в режиме проекта или в режиме в сети.  
  
 Так как изменения производятся на развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети, то проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который был использован для развертывания, станет устаревшим. Если разработчик производит какие-либо изменения в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и пытается развернуть измененный проект, ему будет задан вопрос о перезаписи существующей базы данных. Если разработчик перезаписывает базу данных полностью, это тоже должно быть обработано. Этот вопрос становится сложнее, если изменения производятся прямо на развернутой базе данных персоналом, который не взаимодействовал с командой разработки, вследствие чего не может понять, почему изменения не отражаются в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Существует несколько способов использования средств служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SQL 2005, которые позволяют избежать проблем, возникающих в такой ситуации.  
  
-   Метод 1. Где бы ни были произведены изменения в рабочей версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , используйте среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для создания нового проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , основанного на измененной версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Такой новый проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может проверяться в системе управления версиями, как главная копия проекта. Этот метод будет работать независимо от того, будут ли изменения производиться в режиме в сети в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
-   Метод 2. Изменения производятся только в рабочей версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта. В этом случае можно использовать параметры, доступные в мастере развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , для сохранения изменений, выполненных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], таких как роли безопасности и настройки хранилищ. Это гарантирует, что настройки уровня разработки будут содержаться в файле проекта (настройки хранилищ и роли безопасности могут быть пропущены), а для настроек хранилищ и ролей безопасности будет использован сервер в сети.  
  
-   Метод 3. Изменения производятся только в рабочей версии базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети. Так как обе эти среды работают с одним и тем же сервером в сети, возможности получения различных несинхронизированных версий нет.  
  
  
