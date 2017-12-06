---
title: "Предварительные условия для использования учебников (построитель отчетов) | Документы Майкрософт"
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: "11"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: bc2107402e15e67c68815580a11d4f427db310c0
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Предварительные условия для использования учебников (построитель отчетов)

При прохождении учебников по построителю отчетов требуется возможность просмотра и сохранения отчетов [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] с разбивкой на страницы на сервере отчетов или сайте SharePoint, интегрированном с сервером отчетов. Во всех учебниках для данных используются запросы, которые необходимо обработать с помощью экземпляра SQL Server.  
  
Если нет доступа к серверу отчетов, сайту или источнику данных, изучить работу с построителем отчетов можно путем построения отчета вне сети. См. раздел [Учебник. Создание стандартного отчета с диаграммой в режиме "вне сети" (построитель отчетов)](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  

## <a name="requirements"></a>Требования

Чтобы завершить учебники по построителю отчетов, должны быть выполнены следующие условия.  
  
-   Доступ к построителю отчетов. Построитель отчетов можно запустить с сервера отчетов [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] или сервера отчетов [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Для других серверов отличается только первый шаг — открытие построителя отчетов.  
  
    На сервере отчетов выберите пункт **Создать** > **Отчет с разбивкой на страницы**.
  
    На сервере отчетов в режиме интеграции с SharePoint на вкладке **Документы** выберите пункт **Создать документ**, а затем в раскрывающемся списке выберите пункт **Отчет в построителе отчетов**. Например, `http://<servername>/sites/mySite/reports`. Администратор сайта SharePoint должен включить функцию «Отчет построителя отчетов» для всех библиотек документов.  
  
-   URL-адрес сервера отчетов служб [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] или сайта SharePoint, интегрированного с сервером отчетов служб [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] . Необходимы следующие разрешения: на сохранение и просмотр отчетов, общих источников данных, общих наборов данных, элементов отчетов и моделей. По умолчанию URL-адрес сервера отчетов — `http://<servername>/reportserver`. По умолчанию URL-адрес сайта SharePoint — `http://<sitename>` или `http://<server>/site`.  
  
-   Имя экземпляра SQL Server и учетные данные, необходимые для доступа только для чтения к базе данных. Запросы набора данных в учебниках используют статические данные, но все запросы должны обрабатываться экземпляром SQL Server для возвращения метаданных, необходимых для набора данных отчета. Например, следующая строка подключения определяет только сервер: `data source=<servername>`. У вас должны быть права на доступ к базе данных по умолчанию, назначенной вам системным администратором, который предоставляет разрешения на доступ к серверу. Также можно указать базу данных, как показано в следующей строке подключения: `data source=<servername>;initial catalog=<database>`.  
  
-   Для работы с [учебником по отчету-карте (построитель отчетов)](Tutorial:%20Map%20Report%20\(Report%20Builder\).md) сервер отчетов необходимо настроить для поддержки карт Bing в качестве фона. Дополнительные сведения см. в разделе [План поддержки отчетов-карт](http://msdn.microsoft.com/en-us/5ddc97a7-7ee5-475d-bc49-3b814dce7e19).   

-   В рамках учебника [Создание детализированных и главных отчетов (построитель отчетов)](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md) требуется доступ к кубу Contoso Sales. Дополнительные сведения см. в учебнике. 
  
Администратор сервера отчетов может предоставить необходимые разрешения на сервере отчетов, настроить папки для служб [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] , а также параметры по умолчанию для построителя отчетов. Дополнительные сведения см. в разделе [Установка и удаление построителя отчетов](http://msdn.microsoft.com/library/2c9a5814-17bf-4947-8fb3-6269e7caa416).  

## <a name="next-steps"></a>Следующие шаги

[Учебники по построителю отчетов](../reporting-services/report-builder-tutorials.md)  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
