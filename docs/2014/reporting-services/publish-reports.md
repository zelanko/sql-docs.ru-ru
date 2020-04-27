---
title: Опубликовать отчеты | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86ab056f18e69b0b264525377efb0d257ebc2b95
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108032"
---
# <a name="publish-reports"></a>Публикация отчетов
  Среда[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]позволяет опубликовать либо все отчеты и общие источники данных проекта "Сервер отчетов" на сервере отчетов в процессе развертывания проекта, либо один отчет. Перед публикацией отчета необходимо указать URL-адрес целевого сервера отчетов. Дополнительные сведения см. в разделе [Задание свойства развертывания (службы Reporting Services)](tools/set-deployment-properties-reporting-services.md).  
  
 Можно использовать версию [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для открытия, изменения, предварительного просмотра, сохранения и публикации отчетов как [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] , так и [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] . Дополнительные сведения см. в разделе [Развертывание и поддержка версий в SQL Server Data Tools (службы SSRS)](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
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
 [Поиск, просмотр отчетов и управление ими &#40;построитель отчетов и SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Экспорт отчетов &#40;построитель отчетов и SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
