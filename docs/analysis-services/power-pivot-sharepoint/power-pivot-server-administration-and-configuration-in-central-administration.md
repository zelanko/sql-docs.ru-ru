---
title: "Power Pivot Администрирование и настройка сервера в центре администрирования | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cdbfdc5-45a9-4000-a03d-318cc7ac8fe9
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3dd5476281506f84282fb8b6b6a534820ebea078
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="power-pivot-server-administration-and-configuration-in-central-administration"></a>Настройка и администрирование сервера Power Pivot в центре администрирования
  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] осуществляется администраторами приложения службы SharePoint с помощью центра администрирования SharePoint.  
  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] для SharePoint его необходимо настроить. После установки [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] для SharePoint из программы установки SQL Server его необходимо настроить с помощью  
  
-   [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] или инструмента настройки [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] для SharePoint 2013.  
  
-   Центр администрирования SharePoint  
  
-   Командлеты PowerShell  
  
 Все три подхода позволяют создать полностью настроенный сервер.  
  
 В этом разделе описано, как настроить ПО в центре администрирования. Необходимо выполнить все три обязательные задачи по настройке из нижеприведенного списка.  
  
> [!IMPORTANT]  
>  При работе с фермой SharePoint 2010 необходимо установить SharePoint 2010 с пакетом обновления 1 (SP1), чтобы иметь возможность настроить [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] для SharePoint или ферму SharePoint, в которой используется сервер базы данных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] . Если пакет обновления еще не установлен, установите его перед тем, как начать настройку сервера.  
  
## <a name="benefits-of-configuring-power-pivot-for-sharepoint-using-central-administration"></a>Преимущества настройки Power Pivot для работы с SharePoint в центре администрирования.  
 Центр администрирования SharePoint — это приложение для администрирования фермы SharePoint. Если вы являетесь администратором фермы, то, возможно, предпочтете воспользоваться привычным приложением, чтобы добавить [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] для экземпляра SharePoint в ферму.  
  
 В отличие от инструментов настройки [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] или командлетов PowerShell, на страницах центра администрирования представлен полный набор параметров, которые можно задать при настройке приложения или сервера. При использовании других подходов либо процесс настройки выполняется за меньшее количество шагов, либо требуется предварительное знание методов настройки сервера SharePoint с помощью PowerShell.  
  
## <a name="related-content"></a>См. также  
 [Настройка PowerPivot с помощью Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)  
  
 [Средства настройки PowerPivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Ссылка|Тип|Описание задачи|  
|----------|----------|----------------------|  
|[Развертывание решений PowerPivot в SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)|Обязательно|В этом шаге выполняется установка файлов решения, при котором файлы программы и страницы приложения добавляются в ферму и в семейство веб-сайтов.|  
|[Создание и настройка приложения службы PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)|Обязательно|На этом шаге выполняется подготовка системной службы [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] .|  
|[Включение интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)|Обязательно|На этом шаге выполняется включение функций [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] на уровне коллекций сайтов.|  
|[Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services](../../analysis-services/power-pivot-sharepoint/add-msolap-5-as-a-trusted-data-provider-in-excel-services.md)|Обязательно|На этом шаге поставщик OLE DB служб Analysis Services добавляется как надежный поставщик в службах Excel.|  
|[Обновление данных Power Pivot в SharePoint 2010](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)|Рекомендуемая|Использование обновления данных необязательно, но рекомендуется. Это позволяет задать расписание автоматических обновлений данных [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] в опубликованных книгах Excel.|  
|[Настройка учетной записи автоматического обновления данных Power Pivot (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)|Рекомендуемая|На этом шаге заводится специальная учетная запись, которая может быть использована для запуска заданий обновления данных на сервере.|  
|[Настройка сбора данных об использовании с PowerPivot для SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)|Необязательно|Сбор данных об использовании настраивается по умолчанию. Эти шаги можно использовать для изменения настроек по умолчанию.|  
|[Настройка выделенного обновления данных или обработки только запросов (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/5e027605-1086-4941-bb01-f315df8f829b)|Необязательно|Можно выделить экземпляр [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] только для заданий или запросов обновления данных. Кроме того, можно изменить настройки по умолчанию для параллельных заданий обновления данных.|  
|[Настройка учетных записей служб Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)|Необязательно|Пояснение для обновления паролей или для изменения учетных записей, используемых службами.|  
|[Подключение приложения службы PowerPivot к веб-приложению SharePoint в центре администрирования](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)|Необязательно|В этом разделе приведено описание изменения служебных параметров.|  
|[Создание надежного расположения для сайтов PowerPivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)|Необязательно|В этой статье описано, как добавить коллекцию [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] в качестве надежного расположения.|  
|[Настройка и просмотр файлов журнала SharePoint и журнала диагностики (PowerPivot для SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)|Необязательно|Запись событий в журнал настраивается по умолчанию. Эти шаги можно использовать для изменения настроек по умолчанию.|  
|[Настройка правил определения работоспособности PowerPivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)|Необязательно|Правила для определения исправности сервера настраиваются по умолчанию. Эти шаги помогут изменить некоторые настройки по умолчанию.|  
|[Создание и настройка коллекции Power Pivot](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)|Необязательно|Для установки, настраиваемой вручную, эта процедура описывает, как создать библиотеку коллекции [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] , в которой отображаются эскизы содержащихся в ней книг [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] .|  
|[Добавление типа содержимого соединения для семантической модели бизнес-аналитики в библиотеку (PowerPivot для SharePoint)](../../analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library.md)|Необязательно|Описывает, как следует расширить библиотеку документов так, чтобы она поддерживала создание файлов связи семантической модели.|  
  
## <a name="see-also"></a>См. также  
 [Установка Power Pivot для SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)   
 [Справочник по параметрам конфигурации (PowerPivot для SharePoint)](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Аварийное восстановление PowerPivot для SharePoint](http://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  

