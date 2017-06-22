---
title: "Публикация отчета в библиотеку SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 88caf60aea658972b79c49948d882ce5f96e1d07
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="publish-a-report-to-a-sharepoint-library"></a>опубликовать отчет в библиотеке SharePoint
  Чтобы опубликовать отчет на сайте SharePoint, настроенном для интеграции с SharePoint, необходимо задать свойства проекта в конструкторе отчетов. В свойствах проекта все ссылки на серверы, отчеты и общие источники данных следует указывать в виде полных URL-адресов. В определении отчета все ссылки на вложенные отчеты, детализированные отчеты и такие ресурсы, как изображения, расположенные в Интернете, должны представлять собой полные URL-адреса.  
  
 Необходимо обладать разрешением **Член** или **Владелец** на сайте SharePoint для задания свойств проекта. Дополнительные сведения см. в разделе [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>Публикация отчета на сайте SharePoint  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте существующий или новый проект сервера отчетов.  
  
2.  В меню **Проект** выберите пункт **Свойства**. * \<Проекта >***страницы свойств** откроется диалоговое окно.  
  
3.  В списке **Конфигурация** выберите имя конфигурации сборки решения, предназначенной для формирования и публикации отчета. Текущая конфигурация указана как **Active**(*\<конфигурации >*).  
  
4.  Если в проекте публикуются общие источники данных и перезаписываются ранее опубликованные общие источники данных, присвойте свойству **OverwriteDataSources** значение **True**.  
  
5.  (Необязательно) Для **TargetDataSourceFolder**, введите URL-адрес библиотеки SharePoint или папки библиотеки (например, `http://TestServer/TestSite/Documents/DataSources`).  
  
     Если значение не указано, то будет использовано значение свойства **TargetReportFolder** .  
  
6.  Для **TargetReportFolder**, введите URL-адрес библиотеки или папки библиотеки (например, `http://TestServer/TestSite/Documents/Reports`).  
  
7.  В поле **TargetServerURL**введите URL-адрес сайта SharePoint верхнего уровня или дочернего сайта. Если не указан сайт, то по умолчанию используется сайт верхнего уровня (например, `http://servername`, `http://servername/site` или `http://servername/site/subsite`).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. В обозревателе решений щелкните правой кнопкой мыши отчет, который необходимо опубликовать, и выберите команду **Развернуть**. Отчет будет опубликован в местоположении, которое указано в свойстве **TargetReportFolder**. Ошибки развертывания появляются в окне «Вывод».  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно страниц свойств проекта](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Задание свойства развертывания (службы Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [Публикация отчетов на сервере отчетов](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Использование ODC-файла подключения к данным Office в отчетах (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
