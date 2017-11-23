---
title: "Подключение в режиме в сети для базы данных служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords: Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 40d9f0516485989d7791046c197732bdab103a4a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Подключение в режиме «в сети» к базе данных служб Analysis Services
  Можно напрямую подключиться к существующей базе данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и изменить объекты непосредственно в этой базе данных. При прямом подсоединении к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] изменения объектов происходят моментально и проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не создается в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a>Прямое соединение с базой данных служб Analysis Services с помощью SQL Server Data Tools  
  
1.  Откройте среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** укажите пункт **Открыть** и выберите пункт **База данных служб Analysis Services**.  
  
3.  Выберите **Соединиться с существующей базой данных**.  
  
4.  Укажите имя сервера и имя базы данных.  
  
     Можно либо ввести имя базы данных, либо запросить отображение существующих на сервере баз данных.  
  
5.  Нажмите кнопку **ОК**.  
  
     Теперь можно редактировать любой объект непосредственно в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Работа с проектами и базами данных служб Analysis Services на этапе разработки](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-development.md)   
 [Создание многомерных моделей с помощью SQL Server Data Tools &#40; SSDT &#41;](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
