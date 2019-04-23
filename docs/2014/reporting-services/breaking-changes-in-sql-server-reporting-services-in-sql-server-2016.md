---
title: Критические изменения в SQL Server Reporting Services в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e779a88940db2883846168535e7823c1723f4b4e
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59947660"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2014"></a>Критические изменения в службах SQL Server Reporting Services в выпуске SQL Server «2014»
  В этом разделе описаны критические изменения в службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Такие проблемы могут возникать при обновлении либо в пользовательских скриптах или отчетах. Дополнительные сведения см. в разделе [Использование помощника по обновлению для подготовки к обновлениям](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
 **В этом разделе:**  
  
-   [SQL Server 2014 Reporting Services критические изменения](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services критические изменения](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services критические изменения](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Службы Reporting Services, критические изменения  
 Поведение функций служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] без критических изменений в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Службы Reporting Services, критические изменения  
  
### <a name="sharepoint-mode-server-references-require-the-sharepoint-site"></a>Для ссылки на сервер в режиме интеграции с SharePoint требуется сайт SharePoint  
 Нельзя просматривать непосредственно сервер отчетов (или давать на него прямые ссылки) с помощью виртуального имени в пути URL-адреса. Пример:  
  
 `http://<Server name>/ReportServer`  
  
 Теперь требуется включать сайт SharePoint в путь URL-адреса. Например, если имя узла — "`videos`" и "`sites`" префикс, URL-адрес будет выглядеть следующим образом:  
  
 `http://<Server Name>/sites/videos/_vti_bin/ReportServer`  
  
### <a name="changes-to-sharepoint-mode-command-line-installation"></a>Изменения в процессе установки режима интеграции с SharePoint из командной строки  
 Входной параметр **/RSINSTALLMODE** работает только при установке в собственном режиме и не работает при установке в режиме интеграции с SharePoint. Например, следующее не поддерживается в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]: **/RSINSTALLMODE = «DefaultSharePointMode»**. Указывайте вместо этого входного параметра **/RSSHPINSTALLMODE="DefaultSharePointMode"**.  
  
 Приведенная ниже инструкция представляет пример завершения команд и параметров для установки: **setup/Action = install/Features = SQL, RS/instancename = Denali_INST1 … / rsshpinstallmode = «DefaultSharePointMode»**  
  
 Дополнительные сведения об установке из командной строки см. в разделе [командной строки установки из Reporting Services в режиме SharePoint и собственного режима](install-windows/install-reporting-services-at-the-command-prompt.md).  
  
### <a name="the-reporting-services-wmi-provider-no-longer-supports-configuration-of-sharepoint-mode"></a>Настройка режима интеграции с SharePoint больше не поддерживается поставщиком WMI для служб Reporting Services.  
 Настройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] с SharePoint теперь полностью осуществляется с помощью командлетов SharePoint и центра администрирования SharePoint. Новая архитектура режима интеграции с SharePoint служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] использует архитектуру служб SharePoint. SharePoint не поддерживает интерфейсы WMI.  
  
 В следующем списке указаны компоненты и рабочие процессы, затронутые данными изменениями:  
  
-   Пользовательские приложения, в которых используется поставщик WMI [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
-   Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , rskeymgmt.exe и rsconfig.exe. Вместо использования данных программ для настройки режима интеграции [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] с SharePoint применяйте центр администрирования SharePoint и PowerShell.  
  
-   Среда SQL Server Management Studio: Клиенты не могут ссылаться на сервер с помощью такого синтаксиса, как <machine_name>/<instance_name>. Начиная с выпуска [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] рекомендуемым методом было использование URL-адреса сайта SharePoint. Например **http://<sharepoint_server>/<sharePoint_site>**. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]URL-адрес сайта SharePoint является единственным поддерживаемым синтаксисом.  
  
### <a name="report-model-designer-is-not-available-in-sql-server-data-tools"></a>Конструктор моделей отчетов отсутствует в SQL Server Data Tools  
 Среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] больше не поддерживает проекты моделей отчетов. В службах [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]нет конструктора моделей отчетов. В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] больше нельзя ни создать новый, ни открыть существующий проект модели отчета, создание и обновление моделей отчетов также не поддерживается. Для работы с моделями отчетов можно воспользоваться службами [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] или средствами предыдущих версий. Можно продолжать пользоваться моделями отчетов в качестве источников данных в отчетах, созданных такими средствами служб [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] , как построитель отчетов или конструктор отчетов. Конструктор запросов, с помощью которого создаются запросы для получения данных отчета из модели отчета, будут по-прежнему работать в службах [!INCLUDE[ssSQL11](../includes/sssql11-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services критические изменения  
 В этом разделе описываются критические изменения в службах [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Поскольку SQL Server 2008 R2 содержит изменения дополнительного номера версии по сравнению с SQL Server 2008, рекомендуется также просмотреть содержимое раздела по SQL Server 2008.  
  
### <a name="expanded-csv-data-renderer"></a>Расширен модуль подготовки данных в формате CSV  
 В службах [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]CSV-файл включает данные диаграмм и датчиков. Приложения, которые используют применявшуюся ранее структуру CSV-файлов, больше работать не будут из-за появления дополнительных столбцов для диаграмм и датчиков.  
  
 Дополнительные сведения см. в разделе [Экспорт в CSV-файл &#40;построитель отчетов и службы SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также  
 [Изменения в работе в SQL Server Reporting Services в SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Новые возможности &#40;службы Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Устаревшие функции служб SQL Server Reporting Services в SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Неподдерживаемые возможности в SQL Server Reporting Services в SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
