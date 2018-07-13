---
title: Локальный режим и Подключенном режиме в средстве просмотра отчетов (службы Reporting Services в режиме интеграции с SharePoint) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f1094375d1c911934255878b0e8af6eb7174a761
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157805"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a>Локальный режим и Отчеты, созданные в локальном и подключенном режиме в средстве просмотра отчетов (службы Reporting Services в режиме SharePoint)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] отчеты можно настроить для запуска либо в *локальном режиме* или *в подключенном режиме*, который использует [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов. Вместо этого можно использовать средство просмотра отчетов для подготовки отчетов напрямую из SharePoint, если модуль обработки данных поддерживает локальный режим составления отчетов. Такой подход называется *локальным режимом*. В предыдущих версиях [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], на ферме SharePoint требовалось должен быть подключен к [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] просмотром отчетов мог отчета, сервер настроен в режиме интеграции с SharePoint таким образом элемент управления средства просмотра отчетов. Данный подход называется *удаленным режимом* или *режимом соединения*.  
  
 В *локальном режиме* есть не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов. Необходимо установить [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] надстройка для продуктов SharePoint, но не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов является обязательным. В локальном режиме пользователи могут просматривать отчеты, но не имеют доступа к функциям на стороне сервера, например подпискам и предупреждениям об изменении данных.  
  
||  
|-|  
|**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint|  
  
 **В этом разделе:**  
  
-   [Сравнение локального режима и режима соединения, поддерживаемые расширения](#bkmk_local_vs_connected)  
  
-   [Настройка локального режима и доступ к службам Access в SharePoint 2013](#bkmk_local_mode_sharepoint2013)  
  
-   [Настройка локального режима отчетности в SharePoint 2010](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="bkmk_local_vs_connected"></a> Сравнение локального режима и режима соединения, поддерживаемые расширения  
 **Локальный режим.** Если у вас есть расширение данных, которое поддерживает локальный режим, средство просмотра отчетов напрямую создает отчеты в SharePoint. В *локальном режиме* есть не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов. Необходимо установить [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] надстройка для продуктов SharePoint, но не [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов является обязательным. В локальном режиме пользователи могут просматривать отчеты, но **не** имеют доступа к функциям на стороне сервера, например подпискам и предупреждениям об изменении данных.  
  
 **В подключенном режиме**, называемой *удаленном режиме* требует [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] сервера отчетов в режиме интеграции с SharePoint, подключен к ферме SharePoint, чтобы элемент управления Report Viewer просмотром отчетов мог...  
  
 Ниже приведен список модулей обработки данных, поддерживающих локальный режим составления отчетов.  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Расширение отчетов Access 2010. Дополнительные сведения о службах доступа см. в статье [Использование служб доступа со службами SQL Reporting Services: установка надстройки SQL Server 2008 R2 Reporting Services (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=192686).  
  
-   Модуль обработки данных списка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint. Дополнительные сведения о модуле обработки данных списка SharePoint см. в разделе [источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
 Кроме того, можно разрабатывать пользовательские модули обработки данных с поддержкой локального режима. Дополнительные сведения см. в разделе [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 В локальном режиме поддерживается подготовка к просмотру отчетов с внедренными или общими источниками данных из RSDS-файла. Однако нельзя управлять отчетом или его связанным источником данных. При попытке выполнить это действие возвращается ошибка, сообщающая, что действие не поддерживается в локальном режиме. Управление источниками данных на сайте SharePoint возможно только в подключенном режиме.  
  
> [!NOTE]  
>  Как и в предыдущих версиях, нельзя внедрять имена пользователей и пароли в RSDS-файл.  
  
##  <a name="bkmk_local_mode_sharepoint2013"></a> Настройка локального режима и доступ к службам Access в SharePoint 2013  
 Можно настроить ферму SharePoint 2013 для поддержки существующих сетевых баз данных Access 2010 и локального режима [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Установка и настройка служб Access 2010 для баз данных в сети SharePoint Server 2013](http://technet.microsoft.com/library/ee748653\(office.15\).aspx).  
  
 Нельзя создать новые сетевые базы данных Access для SharePoint 2013. Access 2013 использует базы данных нового типа *Access web app* , создаваемые в Access и затем используемые и публикуемые для общего доступа в виде приложения SharePoint в веб-браузере.  
  
 Дополнительные сведения см. в следующих разделах.  
  
-   [Новые возможности Access 2013](http://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (http://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).  
  
-   [Основные задачи для приложения Access](http://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (http://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500).  
  
##  <a name="bkmk_local_mode_sharepoint2010"></a> Настройка локального режима отчетности в SharePoint 2010  
 Для локального режима требуется состояние сеанса ASP.NET. Установка служб доступа обеспечит предоставление состояний сеансов ASP.Net. Кроме того, можно включить использование PowerShell.  
  
1.  Откройте консоль управления SharePoint 2010.  
  
2.  Введите следующую команду:  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  При появлении соответствующего запроса введите имя базы данных.  
  
4.  Выполните сброс IIS.  
  
 Дополнительные сведения см. в статьях [Использование служб доступа со службами SQL Reporting Services: установка надстройки SQL Server 2008 R2 Reporting Services (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=192686) и [Enable-SPSessionStateService](http://technet.microsoft.com/library/ff607857\(v=office.15\).aspx).  
  
## <a name="connected-mode"></a>режиме соединения  
 Последние сведения об использовании расширения ADS в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] подключенном режиме см. в разделе [отчет служб Access на сайте SharePoint выводит ошибку в данных расширения «ADS»](http://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx).  
  
## <a name="see-also"></a>См. также  
 [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
