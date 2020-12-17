---
title: Отчеты, созданные в локальном и подключенном режимах в средстве просмотра отчетов | Документы Майкрософт
description: Отчеты SQL Server Reporting Services можно настроить для запуска в локальном или подключенном режиме. Сведения о различных режимах.
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016'
ms.openlocfilehash: 76d9f23cb32818c67c34e562b6b1f714a5666c72
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482261"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer"></a>Отчеты, созданные в локальном и подключенном режимах в средстве просмотра отчетов

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчеты можно настроить для запуска либо в *локальном режиме* , либо в *режиме соединения*, который использует сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Вместо этого можно использовать средство просмотра отчетов для подготовки отчетов напрямую из SharePoint, если модуль обработки данных поддерживает локальный режим составления отчетов. Такой подход называется *локальным режимом*. В предыдущих версиях [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ферма серверов SharePoint требовала подключения к серверу отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , настроенному в режиме SharePoint, чтобы элемент управления просмотром отчетов мог их создавать. Данный подход называется *удаленным режимом* или *режимом соединения*.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

 В *локальном режиме* нет сервера отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Необходимо установить дополнение [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint, сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не требуется. В локальном режиме пользователи могут просматривать отчеты, но не имеют доступа к функциям на стороне сервера, например подпискам и предупреждениям об изменении данных.  

## <a name="local-mode-vs-connected-mode-and-supported-extensions"></a>Сравнение локального режима и режима соединения, поддерживаемые расширения

 **Локальный режим.** Если у вас есть расширение данных, которое поддерживает локальный режим, средство просмотра отчетов будет напрямую отображать отчеты из SharePoint. В *локальном режиме* нет сервера отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Необходимо установить дополнение [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint, сервер отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не требуется. В локальном режиме пользователи могут просматривать отчеты, но **не** имеют доступа к функциям на стороне сервера, например подпискам и предупреждениям об изменении данных.  
  
 В **удаленном режиме** или *режиме соединения* требуется наличие сервера отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме SharePoint, который подключен к ферме SharePoint, чтобы элемент управления просмотром отчетов мог их создавать.  
  
 Ниже приведен список модулей обработки данных, поддерживающих локальный режим составления отчетов.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access 2010. Дополнительные сведения о службах доступа см. в статье [Использование служб доступа со службами SQL Reporting Services: установка надстройки SQL Server 2008 R2 Reporting Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686).  
  
-   Модуль обработки данных списка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint. Дополнительные сведения о модуле обработки данных списка SharePoint см. в разделе [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
 Кроме того, можно разрабатывать пользовательские модули обработки данных с поддержкой локального режима. Дополнительные сведения см. в разделе [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 В локальном режиме поддерживается подготовка к просмотру отчетов с внедренными или общими источниками данных из RSDS-файла. Однако нельзя управлять отчетом или его связанным источником данных. При попытке выполнить это действие возвращается ошибка, сообщающая, что действие не поддерживается в локальном режиме. Управление источниками данных на сайте SharePoint возможно только в подключенном режиме.  
  
> [!NOTE]  
>  Как и в предыдущих версиях, нельзя внедрять имена пользователей и пароли в RSDS-файл.  
  
## <a name="configure-local-mode-and-access-services-with-sharepoint-2013"></a>Настройка локального режима и доступ к службам в SharePoint 2013

 Можно настроить ферму SharePoint 2013 для поддержки существующих сетевых баз данных Access 2010 и локального режима [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Установка и настройка служб Access 2010 для баз данных в сети SharePoint Server 2013](https://technet.microsoft.com/library/ee748653\(office.15\).aspx).  
  
 Нельзя создать новые сетевые базы данных Access для SharePoint 2013. Access 2013 использует базы данных нового типа *Access web app* , создаваемые в Access и затем используемые и публикуемые для общего доступа в виде приложения SharePoint в веб-браузере.  
  
 Дополнительные сведения см. в следующих разделах.  
  
-   [Новые возможности Access 2013](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).  
  
-   [Основные задачи для приложения Access](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500).  
  
## <a name="configure-local-mode-reporting-with-sharepoint-2010"></a>Настройка локального режима отчетности в SharePoint 2010

 Для локального режима требуется состояние сеанса ASP.NET. Установка служб доступа обеспечит предоставление состояний сеансов ASP.Net. Кроме того, можно включить использование PowerShell.  
  
1.  Откройте консоль управления SharePoint 2010.  
  
2.  Введите следующую команду:  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  При появлении соответствующего запроса введите имя базы данных.  
  
4.  Выполните сброс IIS.  
  
 Дополнительные сведения см. в статьях [Использование служб доступа со службами SQL Reporting Services: установка надстройки SQL Server 2008 R2 Reporting Services (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) и [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx).  
  
## <a name="connected-mode"></a>режиме соединения

 Последние сведения об использовании расширения ADS в режиме соединения [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в статье [Отчет служб Access на сайте SharePoint выводит ошибку в расширении данных "ADS"](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx).  
  
## <a name="see-also"></a>См. также раздел

 [Источники данных, поддерживаемые службами Reporting Services](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
