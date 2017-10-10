---
title: "Возможности служб Reporting Services узла коллекции | Документы Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 7c86f9ecdbbf4955ba224e40c245fc412742fc30
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-site-collection-features"></a>Возможности служб Reporting Services узла коллекции

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Режим служб Reporting Services для SharePoint предоставляет три компонента коллекции сайтов SharePoint. Эти компоненты поддерживают общие режим SharePoint служб Reporting Services, reporting среды, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], компонент SQL Server 2016 Reporting Services надстройки, и операции управления для служб Reporting Services в центре администрирования SharePoint.

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступны после SQL Server 2016.
  
## <a name="site-collection-features"></a>Компоненты семейства сайтов

 Ниже перечислены компоненты семейства сайтов службы Reporting Services.  
  
|Компонент|Description|  
|-------------|-----------------|  
|**Центр администрирования сервера отчетов**|Включает возможности для управления процессом интеграции с сервером отчетов служб Reporting Services. Этот компонент устанавливается и используется в семействе веб-сайтов центра администрирования SharePoint.<br /><br /> Компонент интеграции сервера отчетов автоматически активируется в семействе веб-сайтов центра администрирования SharePoint после установки надстройки служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] для продуктов SharePoint. В некоторых случаях необходимо вручную активировать компонент. Чтобы активировать компонент сервера отчетов, используйте страницы служб Reporting Services на странице параметров сайта центра администрирования SharePoint.<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Версии служб Reporting Services и более поздней версии надстройки для SharePoint продуктов Активируйте компонент интеграции сервера отчетов для всех существующих коллекциях сайтов при установке надстройки. Кроме того средство автоматически активироваться для новых семейств сайтов.|  
|**Компонент интеграции сервера отчетов**|Обеспечивает широкие возможности отчетов с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] службы Reporting Services<br /><br /> Этот компонент активен по умолчанию.|  
|**Компонент интеграции Power View**|Включает интерактивное исследование данных и визуальное представление для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и табличных баз данных служб Analsysis Services.<br /><br /> Доступ к этому компоненту можно получить через контекстное меню следующих источников данных:<br /><br /> **RDLX;**<br /><br /> **RSDS**<br /><br /> файл соединения с**BISM** .<br /><br /> <br /><br /> Если [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] отсутствует в контекстном меню, убедитесь, что **интеграция Power View** включена.<br /><br /> По умолчанию эта функция отключена.|  

## <a name="next-steps"></a>Следующие шаги

[Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Страницы "Параметры сайта" и "Возможности сайта" служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
