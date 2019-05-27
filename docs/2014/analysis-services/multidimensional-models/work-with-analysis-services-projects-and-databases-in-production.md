---
title: Работа с Analysis Services проектами и базами данных в рабочей среде | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f46a518acb4ba647b5b7bf5503ef76af7b6b90d8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66072432"
---
# <a name="working-with-analysis-services-projects-and-databases-in-a-production-environment"></a>Работа с проектами и базами данных служб Analysis Services в рабочей среде
  После разработки и развертывания базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , необходимо предложить способ выполнения изменений объектов в развернутой базе данных. Некоторые изменения, например связанные с ролями безопасности, секционированием и настройкой хранилищ, можно выполнить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Другие изменения (например, добавление атрибутов и пользовательских иерархий) могут быть выполнены только в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в режиме проекта или в режиме в сети.  
  
 Так как изменения производятся на развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети, то проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , который был использован для развертывания, станет устаревшим. Если разработчик производит какие-либо изменения в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и пытается развернуть измененный проект, ему будет задан вопрос о перезаписи существующей базы данных. Если разработчик перезаписывает базу данных полностью, это тоже должно быть обработано. Этот вопрос становится сложнее, если изменения производятся прямо на развернутой базе данных персоналом, который не взаимодействовал с командой разработки, вследствие чего не может понять, почему изменения не отражаются в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Существует несколько способов использования средств служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] SQL 2005, которые позволяют избежать проблем, возникающих в такой ситуации.  
  
-   Метод 1. При каждом внесении изменений в рабочей версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных, используйте [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для создания нового [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект основан на измененной версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных. Такой новый проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может проверяться в системе управления версиями, как главная копия проекта. Этот метод будет работать независимо от того, будут ли изменения производиться в режиме в сети в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
-   Метод 2. Изменения производятся только в рабочей версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме проекта. В этом случае можно использовать параметры, доступные в мастере развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , для сохранения изменений, выполненных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], таких как роли безопасности и настройки хранилищ. Это гарантирует, что настройки уровня разработки будут содержаться в файле проекта (настройки хранилищ и роли безопасности могут быть пропущены), а для настроек хранилищ и ролей безопасности будет использован сервер в сети.  
  
-   Метод 3: Изменения производятся только в рабочей версии [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базы данных с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в оперативном режиме. Так как обе эти среды работают с одним и тем же сервером в сети, возможности получения различных несинхронизированных версий нет.  
  
  
