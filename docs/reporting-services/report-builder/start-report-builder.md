---
title: "Запуск построителя отчетов | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 56
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e99d13a8e80a0ed2a5e584dcc0e20591507f8c92
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="start-report-builder"></a>Запуск построителя отчетов

[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] является изолированной средой создания отчетов. С ее помощью можно создавать отчеты и публиковать их в среде [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , работающей в основном режиме или режиме интеграции с SharePoint.  
  
 При первом запуске [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] с веб-портала [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint вам будет предложено скачать средство из Центра загрузки Майкрософт. 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 Пользователь или администратор может также [установить построитель отчетов на компьютер из Центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=219138). См. подраздел "Установка построителя отчетов с помощью Systems Manager Server" в разделе [Установка построителя отчетов](../../reporting-services/install-windows/install-report-builder.md) .
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]не устанавливаются при установке SQL Server Reporting Services; необходимо загрузить и установить отдельно.  
  
 Если при запуске [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] на веб-портале или на сайте SharePoint отобразится более ранняя версия [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , обратитесь к администратору, который может обновить версию на веб-портале или сайте SharePoint.  
  
## <a name="to-start-includessrbnoversionincludesssrbnoversion-mdmd-from-the-includessrsnoversionincludesssrsnoversion-mdmd-web-portal"></a>Запуск [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] на веб-портале [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
1.  В веб-браузере введите в адресной строке URL-адрес для сервера отчетов. По умолчанию URL-адрес — http://\<*servername*> / reports.  
  
2.  На верхней панели веб-портала выберите **Создать** > **Отчет с разбиением на страницы**.  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     В первый раз будет предложено [установить построитель отчетов](../../reporting-services/install-windows/install-report-builder.md). 
  
     После этого откроется [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , и можно будет приступить к созданию отчета или открыть отчет с сервера отчетов.  
  
## <a name="to-start-includessrbnoversionincludesssrbnoversion-mdmd-in-sharepoint-integrated-mode"></a>Запуск [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] в режиме интеграции с SharePoint  
  
1.  Перейдите на сайт SharePoint, содержащий нужную библиотеку.  
  
2.  Откройте библиотеку.  
  
3.  Нажмите **Документы**.  
  
4.  В меню **Создать документ** выберите пункт **Отчет построителя отчетов**.  
  
     В первый раз будет запущен мастер [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] для SQL Server. Дополнительные сведения см. в разделе [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) .  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
     **Примечание** . Если меню **Создать документ** не содержит параметры **Отчет построителя отчетов**, **Модель построителя отчетов**или **Источник данных отчета**, необходимо добавить типы их содержимого в библиотеку SharePoint. Дополнительные сведения см. в разделе [Добавление типов содержимого служб Reporting Services в библиотеку SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  

## <a name="next-steps"></a>Следующие шаги

[Построитель отчетов в SQL Server 2016](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
[Определение параметров по умолчанию для построителя отчетов](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
