---
title: Публикация общего источника данных в библиотеку SharePoint | Документы Майкрософт
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 68c556abb719ba9642e7c1074866235e46c1f1e3
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50029123"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a>опубликовать общий источник данных в библиотеке SharePoint
  Чтобы опубликовать общий источник данных на сервере отчетов, работающем в режиме интеграции с SharePoint, необходимо задать свойства проекта отчета в конструкторе отчетов. В свойствах проекта все ссылки на серверы, отчеты и общие источники данных следует указывать в виде полных URL-адресов.  
  
 Необходимо иметь разрешение **Член** или **Владелец** на сайте SharePoint. Дополнительные сведения см. в разделе [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a>Публикация общего источника данных на сайте SharePoint  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте существующий или создайте новый проект сервера отчетов.  
  
2.  В меню **Проект** выберите **Свойства**. Откроется диалоговое окно ****Страницы свойств* \<проект>*.  
  
3.  Выберите **Конфигурацию** для публикации на сайте SharePoint,  
  
4.  Если в проекте публикуются общие источники данных и перезаписываются ранее опубликованные общие источники данных, присвойте свойству **OverwriteDataSources** значение **True**.  
  
5.  Для значения свойства **TargetDataSourceFolder**введите URL-адрес библиотеки SharePoint или папки библиотеки (необязательно). Например: `http://TestServer/TestSite/Documents/DataSources`.  
  
     Если значение не указано, то будет использовано значение свойства **TargetReportFolder** .  
  
6.  В качестве значения свойства **TargetReportFolder**введите URL-адрес библиотеки или папки библиотеки. Например: `http://TestServer/TestSite/Documents/Reports`.  
  
7.  В поле **TargetServerURL**введите URL-адрес сайта SharePoint верхнего уровня или дочернего сайта. Если сайт не указан, то используется сайт верхнего уровня по умолчанию. Например, `http://servername`, `http://servername/site` или `http://servername/site/subsite`.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. В обозревателе решений щелкните правой кнопкой мыши общий источник данных, который необходимо опубликовать, и выберите **Развернуть**. Источник данных будет опубликован в местоположении, которое указывает свойство **TargetDataSourceFolder**. Ошибки развертывания появляются в окне «Вывод».  
  
    > [!NOTE]  
    >  После публикации общего источника данных на сайте SharePoint, расширение имени файла меняется на RSDS. Общий источник данных можно изменять и управлять им непосредственно с сайта SharePoint. Дополнительные сведения см. в разделе [Создание общих источников данных и управление ими (службы Reporting Services в режиме интеграции с SharePoint)](https://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).  
  
## <a name="see-also"></a>См. также:  
 [опубликовать отчет в библиотеке SharePoint](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Диалоговое окно страниц свойств проекта](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Задание свойства развертывания (службы Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [Публикация отчетов на сервере отчетов](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [Использование ODC-файла подключения к данным Office в отчетах (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
