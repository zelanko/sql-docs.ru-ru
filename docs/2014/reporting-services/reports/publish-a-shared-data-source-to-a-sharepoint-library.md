---
title: Публикация общего источника данных в библиотеку SharePoint | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3159e4b64f19410222c6f2adbbce1a1d2c8782e4
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59961200"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a>опубликовать общий источник данных в библиотеке SharePoint
  Чтобы опубликовать общий источник данных на сервере отчетов, работающем в режиме интеграции с SharePoint, необходимо задать свойства проекта отчета в конструкторе отчетов. В свойствах проекта все ссылки на серверы, отчеты и общие источники данных следует указывать в виде полных URL-адресов.  
  
 Необходимо иметь разрешение **Член** или **Владелец** на сайте SharePoint. Дополнительные сведения см. в разделе [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a>Публикация общего источника данных на сайте SharePoint  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте существующий или создайте новый проект сервера отчетов.  
  
2.  В меню **Проект** выберите **Свойства**. Откроется диалоговое окно _Страницы свойств_**\<проекта>**.  
  
3.  Выберите **Конфигурацию** для публикации на сайте SharePoint,  
  
4.  Если в проекте публикуются общие источники данных и перезаписываются ранее опубликованные общие источники данных, присвойте свойству **OverwriteDataSources** значение **True**.  
  
5.  Для значения свойства **TargetDataSourceFolder**введите URL-адрес библиотеки SharePoint или папки библиотеки (необязательно). Например *http://TestServer/TestSite/Documents/DataSources*.  
  
     Если значение не указано, то будет использовано значение свойства **TargetReportFolder** .  
  
6.  В качестве значения свойства **TargetReportFolder**введите URL-адрес библиотеки или папки библиотеки. Например, http:*//TestServer/TestSite/Documents/Reports*.  
  
7.  В поле **TargetServerURL**введите URL-адрес сайта SharePoint верхнего уровня или дочернего сайта. Если сайт не указан, то используется сайт верхнего уровня по умолчанию. Например: http://*имя_сервера*, http://*имя_сервера*/*сайт*или http://*имя_сервера*/*сайт*/*подсайт*.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. В обозревателе решений щелкните правой кнопкой мыши общий источник данных, который необходимо опубликовать, и выберите **Развернуть**. Источник данных будет опубликован в местоположении, которое указывает свойство **TargetDataSourceFolder**. Ошибки развертывания появляются в окне «Вывод».  
  
    > [!NOTE]  
    >  После публикации общего источника данных на сайте SharePoint, расширение имени файла меняется на RSDS. Общий источник данных можно изменять и управлять им непосредственно с сайта SharePoint. Дополнительные сведения см. в разделе [Создание общих источников данных и управление ими (службы Reporting Services в режиме интеграции с SharePoint)](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>См. также  
 [опубликовать отчет в библиотеке SharePoint](publish-a-report-to-a-sharepoint-library.md)   
 [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Диалоговое окно страниц свойств проекта](../tools/project-property-pages-dialog-box.md)   
 [Задание свойства развертывания (службы Reporting Services)](../tools/set-deployment-properties-reporting-services.md)   
 [Публикация отчетов на сервере отчетов](publishing-reports-to-a-report-server.md)   
 [Использование ODC-файла подключения к данным Office в отчетах (службы Reporting Services в режиме интеграции с SharePoint)](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
