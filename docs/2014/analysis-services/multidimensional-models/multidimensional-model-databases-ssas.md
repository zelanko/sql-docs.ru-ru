---
title: Многомерный шаблон баз данных (службы SSAS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
caps.latest.revision: 55
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 97d7364cd9a0fe7901e2357f916d8683dc3b147c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098299"
---
# <a name="multidimensional-model-databases-ssas"></a>Базы данных многомерной модели (службы SSAS)
  База данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — это коллекция источников данных, представлений источников данных, кубов, измерений и ролей. База данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может также включать структуры для интеллектуального анализа данных и пользовательские сборки, позволяющие добавлять в базу данных определяемые пользователем функции.  
  
 Кубы являются базовыми объектами запросов в службах Analysis Services. При подключении к базе данных служб Analysis Services посредством клиентского приложения происходит подключение к кубу внутри этой базы данных. База данных может содержать несколько кубов, если измерения, сборки, роли или структуры интеллектуального анализа используются повторно в разных контекстах.  
  
 Базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно создать программным способом или с помощью одного из следующих интерактивных методов.  
  
-   Разверните проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] на выделенном экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот процесс создает базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , если база данных с таким именем еще не существует на этом экземпляре, а также создает экземпляры сконструированных объектов в созданной базе данных. При работе с базой данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]изменения объектов в проекте [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] вступают в силу только после развертывания проекта на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   Создайте пустую базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], а затем посредством [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] подключитесь напрямую к этой базе данных и создайте объекты в ней (а не в самом проекте). При работе с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] таким образом изменения объектов вступают в силу в базе данных, подключенной на момент сохранения измененного объекта.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует интеграцию с системой управления версиями, обеспечивая поддержку множества разработчиков, работающих одновременно с различными объектами в рамках одного проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Разработчик также может напрямую взаимодействовать с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а не через проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , однако, существует риск того, что объекты базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перестанут синхронизироваться с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , использованным для ее развертывания. После развертывания администрирование базы данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] осуществляется с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Также некоторые изменения можно внести в базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Например, изменения секций и ролей, которые тоже могут привести к потере синхронизации объекта базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , использованным для его развертывания.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Подключение и отключение баз данных служб Analysis Services](attach-and-detach-analysis-services-databases.md)  
  
 [Создание и восстановление резервных копий баз данных служб Analysis Services](backup-and-restore-of-analysis-services-databases.md)  
  
 [Документирование и работа со скриптами в базе данных служб Analysis Services](document-and-script-an-analysis-services-database.md)  
  
 [Изменение или удаление базы данных служб Analysis Services](modify-or-delete-an-analysis-services-database.md)  
  
 [Перемещение базы данных служб Analysis Services](move-an-analysis-services-database.md)  
  
 [Переименование многомерной базы данных &#40;служб Analysis Services&#41;](rename-a-multidimensional-database-analysis-services.md)  
  
 [Уровень совместимости многомерной базы данных &#40;служб Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [Задание свойств многомерной базы данных &#40;служб Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)  
  
 [Синхронизация баз данных служб Analysis Services](synchronize-analysis-services-databases.md)  
  
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>См. также  
 [Подключение в режиме в сети для базы данных служб Analysis Services](connect-in-online-mode-to-an-analysis-services-database.md)   
 [Создание проекта служб Analysis Services &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)   
 [Запрос многомерных данных с помощью многомерных выражений](mdx/querying-multidimensional-data-with-mdx.md)  
  
  