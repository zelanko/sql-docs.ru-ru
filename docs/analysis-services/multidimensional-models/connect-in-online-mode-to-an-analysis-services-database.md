---
title: Подключение в режиме в сети для базы данных служб Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a59d8497fe381e67185c872999687b811715a4eb
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Подключение в режиме «в сети» к базе данных служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
 [Работа с Analysis Services проектами и базами данных на этапе разработки](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-development.md)   
 [Создание многомерных моделей с помощью SQL Server Data Tools & #40; SSDT & #41;](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
