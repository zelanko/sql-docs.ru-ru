---
title: Многомерный шаблон баз данных (службы SSAS) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ec839c9638b3baf79cba0148cc932ead7820f7b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="multidimensional-model-databases-ssas"></a>Базы данных многомерной модели (службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  База данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — это коллекция источников данных, представлений источников данных, кубов, измерений и ролей. База данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может также включать структуры для интеллектуального анализа данных и пользовательские сборки, позволяющие добавлять в базу данных определяемые пользователем функции.  
  
 Кубы являются базовыми объектами запросов в службах Analysis Services. При подключении к базе данных служб Analysis Services посредством клиентского приложения происходит подключение к кубу внутри этой базы данных. База данных может содержать несколько кубов, если измерения, сборки, роли или структуры интеллектуального анализа используются повторно в разных контекстах.  
  
 Базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно создать программным способом или с помощью одного из следующих интерактивных методов.  
  
-   Разверните проект [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] на выделенном экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот процесс создает базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , если база данных с таким именем еще не существует на этом экземпляре, а также создает экземпляры сконструированных объектов в созданной базе данных. При работе с базой данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]изменения объектов в проекте [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] вступают в силу только после развертывания проекта на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   Создайте пустую базу данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], а затем посредством [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] подключитесь напрямую к этой базе данных и создайте объекты в ней (а не в самом проекте). При работе с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] таким образом изменения объектов вступают в силу в базе данных, подключенной на момент сохранения измененного объекта.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует интеграцию с системой управления версиями, обеспечивая поддержку множества разработчиков, работающих одновременно с различными объектами в рамках одного проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Разработчик также может напрямую взаимодействовать с базой данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а не через проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , однако, существует риск того, что объекты базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перестанут синхронизироваться с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , использованным для ее развертывания. После развертывания администрирование базы данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] осуществляется с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Также некоторые изменения можно внести в базу данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Например, изменения секций и ролей, которые тоже могут привести к потере синхронизации объекта базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с проектом служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , использованным для его развертывания.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Присоединение и отсоединение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
 [Создание и восстановление резервных копий баз данных служб Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
 [Document and Script базы данных служб Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
 [Изменение или удаление базы данных служб Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)  
  
 [Перемещение базы данных служб Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 [Переименование многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md)  
  
 [Уровень совместимости многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [Задание свойств многомерной базы данных (службы Analysis Services)](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)  
  
 [Синхронизация баз данных Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>См. также  
 [Подключение в режиме «в сети» к базе данных служб Analysis Services](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)   
 [Создание проекта служб Analysis Services (среда SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)   
 [Запрос многомерных данных с помощью многомерных выражений](../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
  
