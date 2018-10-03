---
title: Публикация отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 39d5c0e2a09926c87669f537710cc44df76b30c0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200754"
---
# <a name="publish-reports"></a>Публикация отчетов
  Из[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], можно опубликовать либо все отчеты и общие источники данных в проекте сервера отчетов на сервере отчетов в процессе развертывания проекта, или можно опубликовать один отчет. Перед публикацией отчета необходимо указать URL-адрес целевого сервера отчетов. Дополнительные сведения см. в разделе [Задание свойства развертывания (службы Reporting Services)](tools/set-deployment-properties-reporting-services.md).  
  
 Можно использовать [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] версии [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для открытия, изменения, предварительного просмотра, сохранения и публикации оба [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] и [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] отчеты. Дополнительные сведения см. в разделе [Развертывание и поддержка версий в SQL Server Data Tools (службы SSRS)](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
### <a name="to-publish-all-reports-in-a-project"></a>Публикация всех отчетов в проекте  
  
-   В меню **Сборка** выберите пункт **Развернуть \<имя проекта отчета>**. Или в обозревателе решений щелкните правой кнопкой мыши проект отчета и выберите команду **Развернуть**. Можно просмотреть состояние процесса публикации в окне вывода.  
  
    > [!NOTE]  
    >  При развертывании проекта «Сервер отчетов» будут развернуты и общие источники данных проекта отчета.  
  
### <a name="to-publish-a-single-report"></a>Публикация одного отчета  
  
-   В обозревателе решений щелкните правой кнопкой мыши отчет, а затем выберите пункт **Развернуть**. Можно просмотреть состояние процесса публикации в окне вывода.  
  
    > [!NOTE]  
    >  При публикации отчета необходимо также выполнить развертывание общих источников данных, которые в нем используются.  
  
## <a name="see-also"></a>См. также  
 [Публикация источников данных и отчетов](reports/publishing-data-sources-and-reports.md)   
 [Предварительный просмотр отчетов](reports/previewing-reports.md)   
 [Публикация отчетов на сервере отчетов](reports/publishing-reports-to-a-report-server.md)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Экспорт отчетов &#40;построитель отчетов и службы SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
