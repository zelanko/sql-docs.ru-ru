---
title: Подключение в режиме "в сети" к базе данных Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 520bf86abe448b444c653f61849640f0b1a7789f
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84536986"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Подключение в режиме «в сети» к базе данных служб Analysis Services
  Можно напрямую подключаться к существующей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базе данных и изменять объекты непосредственно в этой базе данных. При прямом подсоединении к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] изменения объектов происходят моментально и проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не создается в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a>Прямое соединение с базой данных служб Analysis Services с помощью SQL Server Data Tools  
  
1.  Откройте [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** укажите пункт **Открыть** и выберите пункт **База данных служб Analysis Services**.  
  
3.  Выберите **Соединиться с существующей базой данных**.  
  
4.  Укажите имя сервера и имя базы данных.  
  
     Можно либо ввести имя базы данных, либо запросить отображение существующих на сервере баз данных.  
  
5.  Нажмите кнопку **ОК**.  
  
     Теперь можно редактировать любой объект непосредственно в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Работа с Analysis Services проектами и базами данных на этапе разработки](work-with-analysis-services-projects-and-databases-in-development.md)   
 [Создание многомерных моделей с помощью SQL Server Data Tools (SSDT)](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
