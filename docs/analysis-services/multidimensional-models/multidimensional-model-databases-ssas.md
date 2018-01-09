---
title: "Многомерный шаблон баз данных (службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "55"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 854371e81b8adf0ecf32c2685e64f5d136d00987
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="multidimensional-model-databases-ssas"></a>Базы данных многомерной модели (службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Базы данных — это коллекция источников данных, представлений источников данных, кубов, измерений и ролей. База данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может также включать структуры для интеллектуального анализа данных и пользовательские сборки, позволяющие добавлять в базу данных определяемые пользователем функции.  
  
 Кубы являются базовыми объектами запросов в службах Analysis Services. При подключении к базе данных служб Analysis Services посредством клиентского приложения происходит подключение к кубу внутри этой базы данных. База данных может содержать несколько кубов, если измерения, сборки, роли или структуры интеллектуального анализа используются повторно в разных контекстах.  
  
 Базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно создать программным способом или с помощью одного из следующих интерактивных методов.  
  
-   Разверните проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] на выделенном экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот процесс создает базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , если база данных с таким именем еще не существует на этом экземпляре, а также создает экземпляры сконструированных объектов в созданной базе данных. При работе с базой данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]изменения объектов в проекте [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] вступают в силу только после развертывания проекта на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   Создайте пустую базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], а затем посредством [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] подключитесь напрямую к этой базе данных и создайте объекты в ней (а не в самом проекте). При работе с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] таким образом изменения объектов вступают в силу в базе данных, подключенной на момент сохранения измененного объекта.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует интеграцию с системой управления версиями, обеспечивая поддержку множества разработчиков, работающих одновременно с различными объектами в рамках одного проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Разработчик также может напрямую взаимодействовать с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а не через проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , однако, существует риск того, что объекты базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перестанут синхронизироваться с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , использованным для ее развертывания. После развертывания администрирование базы данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] осуществляется с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Также некоторые изменения можно внести в базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Например, изменения секций и ролей, которые тоже могут привести к потере синхронизации объекта базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , использованным для его развертывания.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Подключение и отключение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
 [Документирование и работа со скриптами в базе данных служб Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
 [Изменение или удаление базы данных служб Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)  
  
 [Перемещение базы данных служб Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 [Переименование многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md)  
  
 [Уровень совместимости многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [Задание свойств многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)  
  
 [Синхронизация баз данных служб Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>См. также:  
 [Подключение в режиме «в сети» к базе данных служб Analysis Services](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)   
 [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)   
 [Запрос многомерных данных с помощью многомерных выражений](../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
  
