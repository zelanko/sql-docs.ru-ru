---
title: Планирование создания отчетов и развертывания отчетов (Reporting Services 2014) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 1c1e265e-52a2-4de3-96fd-ca4abae01c02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4347854a56e0d6cb021a3958203d94c28cb96d22
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188493"
---
# <a name="plan-for-report-design-and-report-deployment-reporting-services-2014"></a>Запланируйте создание и развертывание отчетов (службы Reporting Services 2014)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обеспечивают несколько способов разработки и развертывания отчетов. Используйте приведенную в этом разделе информацию для планирования среды создания отчетов и сервера отчетов, которые будут работать вместе. В этом разделе приводятся общие сведения о поддержке определения отчетов компонентами служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Определение отчета — это XML-файл, написанный на языке определения отчетов (RDL) или на языке определения отчетов для клиентов (RDLC). Каждое определение отчета соответствует определенной версии схемы, указанной в начале файла.  
  
 RDL-файлы разрабатываются в конструкторе отчетов среды [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] и в построителе отчетов 3.0. RDLC-файлы разрабатываются с использованием элементов управления, включенных в среду [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 В этом разделе:  
  
-   [Версии RDL-схем](#bkmk_rdl_schema_versions)  
  
-   [Сервер отчетов и поддержка RDL-схемы](#bkmk_report_server_rdl_schema_support)  
  
-   [Поддержка разработки отчетов и развертывания](#bkmk_report_authoring_and_deployment)  
  
-   [Элементы управления ReportViewer](#bkmk_reportviewer)  
  
##  <a name="bkmk_rdl_schema_versions"></a> Версии RDL-схем  
 В следующей таблице перечисляются все доступные версии схем и сокращения, используемые в остальной части раздела.  
  
|Аббревиатура|Версия схемы|  
|------------------|--------------------|  
|2010 RDL|https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition|  
|2008 RDL|https://schemas.microsoft.com/sqlserver/reporting/2008/01/reportdefinition|  
|2005 RDL<br /><br /> 2005 RDLC|https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition|  
|2000 RDL|https://schemas.microsoft.com/sqlserver/reporting/2003/10/reportdefinition|  
  
 Дополнительные сведения о RDL и RDL-схемах см. в одном из следующих источников:  
  
-   [Схемы XML Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=31850)  
  
-   [Спецификация языка определения отчетов](https://go.microsoft.com/fwlink/?linkid=116865)  
  
-   [Язык определения отчетов (службы SSRS)](reports/report-definition-language-ssrs.md)  
  
 Дополнительные сведения об элементах управления ReportViewer см. в разделе [Элементы управления ReportViewer (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx).  
  
##  <a name="bkmk_report_server_rdl_schema_support"></a> Сервер отчетов и поддержка RDL-схемы  
 Файл определения отчета можно развернуть на сервере отчетов [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] одним из следующих способов.  
  
-   **Конструктор отчетов:** Развертывание отчета из конструктора отчетов в среде [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].  
  
-   **Построитель отчетов:** Сохранение отчета на сервере отчетов из построителя отчетов.  
  
-   **Диспетчер отчетов:** Передача отчета на сервере отчетов в собственном режиме из диспетчера отчетов.  
  
-   **SharePoint:** Передача отчета на сайте SharePoint, настроенной с сервера отчетов в режиме SharePoint.  
  
-   **Программным способом:** Опубликуйте отчет программным образом с помощью API-интерфейсов SOAP на сервере отчетов. Дополнительные сведения см. в разделе [Report Server Web Service](report-server-web-service/report-server-web-service.md).  
  
 В следующей таблице перечислены поддерживаемые версии RDL-схемы по версии сервера отчетов.  
  
|Версия сервера отчетов|Версия схемы языка определения отчетов|  
|---------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> либо<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> либо<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|2010 RDL<br /><br /> 2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]|2005 RDL<br /><br /> 2000 RDL|  
  
 Если определение отчета публикуется на сервере отчетов или выполняется обновление сервера отчетов, то сервер отчетов сохранит определение отчета в первоначальном формате. **При первом использовании**сервер отчетов обновит отчет в базе данных сервера отчетов, преобразовав его в двоичный формат, который будет сохранен для использования при последующих просмотрах. Само определение отчетов (RDL-файл) не обновляется.  
  
 На сервере отчетов можно извлечь доступную только для чтения копию файла определения отчета (RDL-файл). На сервере отчетов, работающем в собственном режиме, перейдите к диспетчеру отчетов, выберите отчет и нажмите кнопку **Загрузить**. При развертывании в режиме интеграции с SharePoint перейдите в библиотеку документов, выберите отчет и нажмите кнопку **Загрузить копию**.  
  
 Для обновления определения отчета его следует открыть в среде разработки отчетов, а затем сохранить.  
  
 Дополнительные сведения о поддерживаемых версиях схем и обновлениях отчетов см. в разделе [Обновление отчетов](install-windows/upgrade-reports.md).  
  
##  <a name="bkmk_report_authoring_and_deployment"></a> Поддержка разработки и развертывания отчетов  
 Среды разработки отчетов: конструктор отчетов в проектах [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] и построитель отчетов. Среды разработки отчетов предоставляют разнообразную поддержку обновления, разработки и развертывания отчетов, а также их предварительного просмотра в локальном режиме и на сервере отчетов.  
  
 В следующей таблице приводятся сведения о поддержке разработки и развертывания определений отчетов для различных версий схемы.  
  
|Среда разработки|RDL-версия разработчика|RDL-версия для развертывания|Развертывается на версиях сервера отчетов|  
|---------------------------|--------------------------|------------------------|--------------------------------------|  
|Конструктор отчетов из SQL Server Data Tools 2014 — бизнес-аналитика для Microsoft Visual Studio 2012, в центре загрузки Майкрософт.<br /><br /> или<br /><br /> Конструктор отчетов из SQL Server Data Tools 2012 — бизнес-аналитика для Microsoft Visual Studio 2012, в центре загрузки Майкрософт.<br /><br /> Или<br /><br /> Конструктор отчетов в среде [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools, включенный в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].|Разработчики 2010 RDL. При открытии существующего RDL-файла.<br /><br /> 2000 RDL, обновляется до 2010 RDL<br /><br /> 2005 RDL, обновляется до 2010 RDL<br /><br /> 2008 RDL, обновляется до 2010 RDL|2008 RDL<br /><br /> 2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|Конструктор отчетов в среде [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio|Разработчики 2010 RDL. При открытии существующего RDL-файла.<br /><br /> 2000 RDL, обновляется до 2010 RDL<br /><br /> 2005 RDL, обновляется до 2010 RDL<br /><br /> 2008 RDL, обновляется до 2010 RDL|2008 RDL<br /><br /> 2010 RDL|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|Конструктор отчетов в среде [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio|Разработчики 2008 RDL. При открытии существующего RDL-файла.<br /><br /> 2000 RDL, обновляется до 2008 RDL<br /><br /> 2005 RDL, обновляется до 2008 RDL|2008 RDL|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|  
|Построитель отчетов [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]|Разработчики 2010 RDL. При открытии существующего RDL-файла.<br /><br /> 2000 RDL, обновляется до 2010 RDL<br /><br /> 2005 RDL, обновляется до 2010 RDL<br /><br /> 2008 RDL, обновляется до 2010 RDL|2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|  
|Конструктор отчетов Visual Studio RDLC|2005 RDLC|Н/Д|Н/Д|  
  
 Дополнительные сведения о [!INCLUDE[ss_dtbi_vs2013](../includes/ss-dtbi-vs2013-md.md)]см. в следующих разделах:  
  
-   [Развертывание и поддержка версий в SQL Server Data Tools (службы SSRS)](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
-   [Microsoft SQL Server Data Tools ― Business Intelligence для Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843).  
  
##  <a name="bkmk_reportviewer"></a> Элементы управления ReportViewer  
 Элемент управления ReportViewer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] может отображать RDLC-отчет в режиме локального предварительного просмотра или в удаленном режиме. Этот элемент управления может отображать RDL-файл, размещенный на сервере отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Следующая таблица содержит список версий языка определения отчетов, поддерживаемых элементами управления ReportViewer для локальной обработки (RDLC). Сводку по поддержке языка определения отчетов на стороне сервера см. в разделе [Сервер отчетов и поддержка RDL-схемы](#bkmk_report_server_rdl_schema_support).  
  
|Элемент управления ReportViewer в продукте|Версии языка определения отчетов для локального предварительного просмотра|  
|-------------------------------------|--------------------------------------|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2013<br /><br /> либо<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2012<br /><br /> либо<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]|2008 RDL|  
|[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]<br /><br /> либо<br /><br /> [!INCLUDE[vsOrcas](../includes/vsorcas-md.md)]|2005 RDL|  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Преобразование RDLC-файлов в RDL-файлы](https://msdn.microsoft.com/library/ms252109.aspx)  
  
-   [Элементы управления ReportViewer (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx)  
  
-   [Добавление и настройка элементов управления ReportViewer](https://msdn.microsoft.com/library/ms252104.aspx)  
  
## <a name="see-also"></a>См. также  
 [Отчеты, элементы отчетов и определения отчетов (построитель отчетов и службы SSRS)](report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Инструментальные средства служб Reporting Services](tools/reporting-services-tools.md)   
 [Язык определения отчетов (службы SSRS)](reports/report-definition-language-ssrs.md)  
  
  
