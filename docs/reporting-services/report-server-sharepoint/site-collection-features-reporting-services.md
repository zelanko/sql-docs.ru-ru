---
title: Компоненты семейства веб-сайтов служб Reporting Services | Документы Майкрософт
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 2610ac04f49ccfd39f1e752ecdc03376c05285fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773844"
---
# <a name="reporting-services-site-collection-features"></a>Компоненты семейства веб-сайтов служб Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Службы Reporting Services в режиме интеграции с SharePoint предоставляют три компонента семейства веб-сайтов SharePoint. Эти компоненты поддерживают среду создания отчетов служб Reporting Services в режиме интеграции с SharePoint, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], компонент надстройки служб SQL Server 2016 Reporting Services и операции управления для служб Reporting Services в центре администрирования SharePoint.

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.
  
## <a name="site-collection-features"></a>Компоненты семейства веб-сайтов

 В представленной ниже таблице описываются компоненты семейства веб-сайтов служб Reporting Services.  
  
|Компонент|Описание|  
|-------------|-----------------|  
|**Центр администрирования сервера отчетов**|Включает возможности для управления интеграцией с сервером отчетов служб Reporting Services. Этот компонент устанавливается и используется в семействе веб-сайтов центра администрирования SharePoint.<br /><br /> Компонент интеграции сервера отчетов автоматически активируется в семействе веб-сайтов центра администрирования SharePoint после установки надстройки служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] для продуктов SharePoint. В некоторых ситуациях необходимо активировать этот компонент вручную. Чтобы активировать компонент сервера отчетов, используйте страницы служб Reporting Services на странице параметров сайта в центре администрирования SharePoint.<br /><br /> Версия служб [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Reporting Services и более поздние версии надстройки для продуктов SharePoint активируют функцию интеграции сервера отчетов для всех семейств веб-сайтов, существующих на момент установки надстройки. Кроме того, эта функция автоматически активируется для новых семейств веб-сайтов.|  
|**Компонент интеграции сервера отчетов**|Обеспечивает создание улучшенных отчетов с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] Reporting Services.<br /><br /> Этот компонент активен по умолчанию.|  
|**Компонент интеграции Power View**|Включает интерактивное исследование данных и визуальное представление для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и табличных баз данных служб Analsysis Services.<br /><br /> Доступ к этому компоненту можно получить через контекстное меню следующих источников данных:<br /><br /> **RDLX;**<br /><br /> **RSDS**<br /><br /> файл соединения с**BISM** .<br /><br /> <br /><br /> Если [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] отсутствует в контекстном меню, убедитесь, что **интеграция Power View** включена.<br /><br /> По умолчанию эта функция отключена.|  

## <a name="next-steps"></a>Следующие шаги

[Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Страницы "Параметры сайта" и "Возможности сайта" служб Reporting Services (режим интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[активировать функции синхронизации файлов сервера отчетов в центре администрирования SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
