---
title: "Запуск построителя отчетов | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Построитель отчетов, запуск"
  - "запуск построителя отчетов"
  - "Интеграция с SharePoint [службы Reporting Services], запуск построителя отчетов"
  - "запуск построителя отчетов"
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 56
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 56
---
# Запуск построителя отчетов
  Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] является изолированной средой создания отчетов. С ее помощью можно создавать отчеты и публиковать их в среде [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], работающей в основном режиме или режиме интеграции с SharePoint.  
  
 При первом запуске [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] с веб-портала [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint вам будет предложено скачать средство из Центра загрузки Майкрософт. 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 Пользователь или администратор может также [установить построитель отчетов на компьютер из Центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=219138). См. подраздел "Установка построителя отчетов с помощью Systems Manager Server" в разделе [Установка построителя отчетов](../../reporting-services/install-windows/install-report-builder.md).
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] не устанавливается вместе с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Его необходимо скачать и установить отдельно.  
  
 Если при запуске [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] на веб-портале или на сайте SharePoint отобразится более ранняя версия [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , обратитесь к администратору, который может обновить версию на веб-портале или сайте SharePoint.  
  
## Запуск [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] на веб-портале [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
1.  В веб-браузере введите в адресной строке URL-адрес для сервера отчетов. URL-адрес по умолчанию — http://\<*имя_сервера*>/reports.  
  
2.  На верхней панели веб-портала выберите **Создать** > **Отчет с разбиением на страницы**.  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     В первый раз будет предложено [установить построитель отчетов](../../reporting-services/install-windows/install-report-builder.md). 
  
     После этого откроется [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)], и можно будет приступить к созданию отчета или открыть отчет с сервера отчетов.  
  
## Запуск [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] в режиме интеграции с SharePoint  
  
1.  Перейдите на сайт SharePoint, содержащий нужную библиотеку.  
  
2.  Откройте библиотеку.  
  
3.  Нажмите **Документы**.  
  
4.  В меню **Создать документ** выберите пункт **Отчет построителя отчетов**.  
  
     В первый раз будет запущен мастер [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] для SQL Server. Дополнительные сведения см. в разделе [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) .  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , и можно будет приступить к созданию отчета или открыть отчет на сервере отчетов.  
  
     **Примечание** . Если меню **Создать документ** не содержит параметры **Отчет построителя отчетов**, **Модель построителя отчетов**или **Источник данных отчета**, необходимо добавить типы их содержимого в библиотеку SharePoint. Дополнительные сведения см. в разделе [Добавление типов содержимого служб Reporting Services в библиотеку SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
## См. также  
 [Построитель отчетов в SQL Server 2016](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [Задание параметров по умолчанию для построителя отчетов](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  
  
  