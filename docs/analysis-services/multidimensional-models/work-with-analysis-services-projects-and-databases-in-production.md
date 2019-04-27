---
title: Работа с проектами и базами данных в рабочей среде служб Analysis Services | Документация Майкрософт
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743240"
---
# <a name="work-with-analysis-services-projects-and-databases-in-production"></a>Работа с проектами и базами данных в рабочей среде служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  После разработки и развертывания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , необходимо предложить способ выполнения изменений объектов в развернутой базе данных. Некоторые изменения, например связанные с ролями безопасности, секционированием и настройкой хранилищ, можно выполнить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Другие изменения (например, добавление атрибутов и пользовательских иерархий) могут быть выполнены только в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в режиме проекта или в режиме в сети.  
  
 Так как изменения производятся на развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети, то проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который был использован для развертывания, станет устаревшим. Если разработчик производит какие-либо изменения в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и пытается развернуть измененный проект, ему будет задан вопрос о перезаписи существующей базы данных. Если разработчик перезаписывает базу данных полностью, это тоже должно быть обработано. Этот вопрос становится сложнее, если изменения производятся прямо на развернутой базе данных персоналом, который не взаимодействовал с командой разработки, вследствие чего не может понять, почему изменения не отражаются в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Существует несколько способов использования средств служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SQL 2005, которые позволяют избежать проблем, возникающих в такой ситуации.  
  
-   Метод 1. При каждом внесении изменений в рабочей версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных, используйте [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для создания нового [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект основан на измененной версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. Такой новый проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может проверяться в системе управления версиями, как главная копия проекта. Этот метод будет работать независимо от того, будут ли изменения производиться в режиме в сети в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
-   Метод 2. Изменения производятся только в рабочей версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта. В этом случае можно использовать параметры, доступные в мастере развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , для сохранения изменений, выполненных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], таких как роли безопасности и настройки хранилищ. Это гарантирует, что настройки уровня разработки будут содержаться в файле проекта (настройки хранилищ и роли безопасности могут быть пропущены), а для настроек хранилищ и ролей безопасности будет использован сервер в сети.  
  
-   Метод 3: Изменения производятся только в рабочей версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в оперативном режиме. Так как обе эти среды работают с одним и тем же сервером в сети, возможности получения различных несинхронизированных версий нет.  
  
  
