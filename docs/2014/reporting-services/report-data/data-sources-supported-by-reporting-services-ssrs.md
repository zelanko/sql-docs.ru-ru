---
title: Источники данных, поддерживаемые службами Reporting Services (SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SQL Server data processing extension [Reporting Services]
- XML data processing extension [Reporting Services]
- reports [Reporting Services], data
- data processing extensions [Reporting Services], data sources
- Oracle [Reporting Services]
- OLE DB data processing extension
- data sources [Reporting Services], about data sources
- ODBC data processing extension
- Reporting Services, data sources
ms.assetid: 9d11d055-a3be-45aa-99a7-46447a94ed42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 87cc2d927bc3a0786e935e2cd20c669a8bfac87a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63461727"
---
# <a name="data-sources-supported-by-reporting-services-ssrs"></a>Источники данных, поддерживаемые службами Reporting Services (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] получают через модульный и расширяемый уровень данных, где работают модули обработки данных. Для получения данных отчета из источника данных необходимо выбрать модуль обработки данных, поддерживающий как тип источника данных, так и версию программного обеспечения источника данных и его платформу (32-разрядная или 64-разрядная [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]).  
  
 При развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]набор модулей обработки данных, предоставляющих доступ к различным типам источников данных, автоматически устанавливается и регистрируется как в системе создающего отчеты клиента, так и на сервере отчетов. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливают следующие типы источников данных.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для многомерных Выражений, расширений интеллектуального анализа данных, [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerPivot и табличных моделей  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Parallel Data Warehouse  
  
-   Oracle;  
  
-   SAP NetWeaver BI  
  
-   [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint  
  
-   Teradata  
  
-   OLE DB  
  
-   интерфейс ODBC  
  
-   XML  
  
 Кроме того, системный администратор может установить и зарегистрировать пользовательские модули обработки данных и стандартные поставщики данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Для обработки и просмотра отчета модули обработки данных и поставщики данных должны быть установлены и зарегистрированы на сервере отчетов. Для предварительного просмотра отчета их также необходимо установить и зарегистрировать на клиенте, где производится создание отчетов. Модули обработки данных и поставщики данных должны быть скомпилированы в собственном коде для той платформы, на которую устанавливаются. Если развертывание источника данных производится программными средствами с помощью веб-службы SOAP, необходимо определить модуль источника данных. Используйте значения модуля обработки данных из файла **RSReportDesigner.config** . По умолчанию файл находится в следующей папке:  
  
```  
<drive letter>\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
```  
  
 Например, модуль обработки данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] представляет собой OLEDB-MD.  
  
 Многие стандартные поставщики данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сторонних производителей можно скачать в [Центре загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=51456) и на сайтах сторонних производителей. Сведения о поставщиках данных сторонних производителей можно найти также в общедоступном форуме по службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
> [!NOTE]  
>  Стандартные поставщики данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] необязательно поддерживают все функции, предоставляемые модулями обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Кроме того, некоторые поставщики данных OLE DB и драйверы ODBC могут быть использованы для создания и предварительного просмотра отчетов, но не поддерживают отчеты, опубликованные на сервере отчетов. Например, поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet не поддерживается на сервере отчетов. Дополнительные сведения см. в разделе [Модули обработки данных и поставщики данных .NET Framework (службы SSRS)](data-processing-extensions-and-net-framework-data-providers-ssrs.md).  
  
 Дополнительные сведения о развертывании специализированных модулей обработки данных см. в разделе [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md). Дополнительные сведения о стандартных поставщиках данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе по пространству имен <xref:System.Data> .  
  
 Дополнительные сведения о модулях обработки данных, поддерживаемых построителем отчетов, см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [документации по построителю отчетов](https://go.microsoft.com/fwlink/?LinkId=154494) на сайте msdn.microsoft.com.  
  
## <a name="platform-support-for-report-data-sources"></a>Поддержка платформ источников данных отчета  
 Источники данных, которые вы можете использовать в развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , различаются в зависимости от выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и платформы. Дополнительные сведения о функциях см. в разделе [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Приведенная далее в разделе таблица содержит сведения о поддерживаемых источниках данных в зависимости от версии и платформы.  
  
 Требования к платформам для источников данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] различаются для системы клиента, создающего отчеты, и сервера отчетов.  
  
### <a name="on-the-report-authoring-client"></a>На системе клиента, создающего отчеты  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] — это 32-разрядное приложение. [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] не поддерживается на платформе Itanium. На платформе x64 для изменения и предварительного просмотра отчетов в конструкторе отчетов необходимо наличие 32-разрядных версий поставщиков данных, установленных в каталоге платформы (x86).  
  
### <a name="on-the-report-server"></a>На сервере отчетов  
 При развертывании отчета на 64-разрядной версии сервера отчетов (на базе x86) на нем должны быть установлены 64-разрядные версии поставщиков данных, скомпилированные в собственном коде для конкретной платформы. Упаковка 32-разрядной версии поставщика данных в 64-разрядные интерфейсы не поддерживается. Дополнительные сведения см. в документации по поставщику данных.  
  
## <a name="supported-data-sources"></a>Поддерживаемые источники данных  
 В следующей таблице перечислены поставщики данных и модули обработки данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] , которые могут использоваться для получения данных для наборов данных и моделей отчетов. Дополнительные сведения о модуле обработки данных или поставщике данных можно получить, перейдя по ссылке во втором столбце. Столбцы таблицы содержат следующие сведения:  
  
-   Источник данных отчета: Тип данных, доступ к; например реляционную базу данных, многомерной базы данных, неструктурированный файл или XML. Этот столбец отвечает на вопрос: «Типы данных можно [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использоваться в отчете?»  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Тип источника данных: Один из типов источников данных, содержащихся в раскрывающемся списке при определении источника данных в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Этот список содержит установленные и зарегистрированные модули обработки данных и поставщики данных. Этот столбец отвечает на вопрос: «Какие типы источников данных можно выбрать из раскрывающегося списка при создании источника данных отчета?»  
  
-   Имя поставщика данных и расширения обработки данных: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Модуль обработки данных или другой поставщик данных, который соответствует [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] выбранному типу источника данных. Этот столбец отвечает на вопрос: «При выборе типа источника данных используется какие соответствующего поставщика данных или расширения обработки данных?»  
  
-   Версия базового поставщика данных (необязательно): Некоторые типы источников данных поддерживают несколько поставщиков данных. Это могут быть как разные версии одного и того же поставщика, так и разные реализации этого типа поставщика данных от сторонних производителей. Имя этого поставщика зачастую появляется в строке соединения после настройки источника данных. Этот столбец отвечает на вопрос: "Какой поставщик данных можно выбрать в диалоговом окне **Свойства соединения** после выбора типа источника данных?"  
  
-   Платформа *\<источника данных*: Платформа источника данных, поддерживаемые поставщиком данных или расширения обработки данных для целевого источника данных. Этот столбец отвечает на вопрос: «Можно этот обработки данных расширения или поставщик данных получать данные из источника данных на платформе этого типа?»  
  
-   Версия источника данных: Версия целевого источника данных, поддерживаемых поставщиком модуль Обработки данных. Этот столбец отвечает на вопрос: «Можно этот обработки данных расширения или поставщик данных получать данные из этой версии источника данных?»  
  
-   Платформа *\<RS*: Платформы сервера отчетов и клиента, создающего которых можно установить пользовательский модуль Обработки или поставщик данных. Встроенные модули обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] всегда устанавливаются вместе со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Специализированный модуль обработки данных или поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] должен быть скомпилирован в виде собственного кода для конкретной платформы. Этот столбец отвечает на вопрос: «Можно этот обработки данных расширения или поставщик данных установить на платформе этого типа?»  
  
###  <a name="DataSourcesTable"></a> Типы источников данных  
  
|Источник<br /><br /> данных отчета|Тип источника данных служб Reporting Services|Имя модуля обработки данных или поставщика данных|Версия базового поставщика данных<br /><br /> (необязательно)|Данные <br /><br /> Source<br /><br /> на платформе x86|Данные<br /><br /> Source<br /><br /> на платформе x64|Версия источника данных|Сервер отчетов<br /><br /> на платформе x86|Сервер отчетов<br /><br /> на платформе x64|  
|-------------------------------|-----------------------------------------|------------------------------------------------------|-------------------------------------------------------|--------------------------------------|--------------------------------------|----------------------------|-------------------------|-------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реляционная база данных|[Microsoft SQL Server](#MicrosoftSQLServer)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.SqlClient|Да|Да|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии.|Да|Да|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реляционная база данных|[OLEDB](#OLEDBSQL)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OledbClient|Да|Да|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии.|Да|Да|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реляционная база данных|[интерфейс ODBC](#ODBC)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OdbcClient|Да|Да|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии.|Да|Да|  
|[!INCLUDE[ssSDS](../../includes/sssds-md.md)]|[База данных Azure SQL для Windows](#Azure)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.SqlClient|Недоступно|Недоступно|[!INCLUDE[ssSDS](../../includes/sssds-md.md)]|Да|Да|  
|[!INCLUDE[ssDW](../../includes/ssdw-md.md)] (модуль)|[Параллельные хранилища данных Microsoft](#PWD)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Н/Д|Недоступно|Недоступно|[!INCLUDE[ssDWfull](../../includes/ssdwfull-md.md)]|Да|Да|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (многомерная база данных)|[Службы Microsoft SQL Server Analysis Services](#AnalysisServices)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Использует ADOMD.NET|Да|Да|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и более поздних версий<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий|Да|Да|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (многомерная база данных)|[OLEDB](#OLEDBAS9)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OledbClient<br /><br /> Версия 10.0|Да|Да|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Да|Да|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (многомерная база данных)|[OLEDB](#OLEDBAS9)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OledbClient<br /><br /> Версия 9,0|Да|Да|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Да|Да|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (многомерная база данных)|OLEDB|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OledbClient<br /><br /> Версия 8.0|Да|Нет|Н/Д|Да|Нет|  
|Списки SharePoint|[Список Microsoft SharePoint](#SharePointList)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Возвращает данные из Lists.asmx или API-интерфейсов объектной модели SharePoint.<br /><br /> См. [примечание](#SharePointList).|Нет|Да|Продукты SharePoint 2013<br /><br /> Продукты SharePoint 2010|Да|Да|  
|Списки SharePoint|[Список Microsoft SharePoint](#SharePointList)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Возвращает данные из Lists.asmx или API-интерфейсов объектной модели SharePoint.<br /><br /> См. [примечание](#SharePointList).|Да|Да|[!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 и [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007|Да|Да|  
|XML|[XML](#XML)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Источники XML-данных не зависят от платформы.|Недоступно|Недоступно|[!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)] или документы|Да|Да|  
|Модель сервера отчетов|Модель отчета|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для опубликованного SMDL-файла|Источники данных для модели используют встроенные модули обработки данных.<br /><br /> Для моделей на основе Oracle требуются клиентские компоненты Oracle.<br /><br /> Для моделей на основе Teradata требуется поставщик данных .NET для Teradata от Teradata.<br /><br /> См. документацию Teradata по поддержке платформ.|Недоступно|Недоступно|Источники создания моделей:[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии<br /><br /> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<br /><br /> Oracle 9.2.0.3 или более поздней версии<br /><br /> Teradata V14, v13, v12 и v6.2|Да|Да|  
|Многомерная база данных SAP|[Sap BI NetWeaver](#SapBINetWeaver)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|См. документацию SAP по поддержке платформ.|Недоступно|Н/Д|SAP BI NetWeaver 3.5|Да|Недоступно|  
|[!INCLUDE[extEssbase](../../includes/extessbase-md.md)]|[Hyperion Essbase](#Hyperion)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|См. документацию Hyperion по поддержке платформ.|Да|Недоступно|[!INCLUDE[extEssbase](../../includes/extessbase-md.md)] 9.3.1|Да|Недоступно|  
|Реляционная база данных Oracle|[Oracle;](#OracleClient)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OracleClient<br /><br /> Необходимы клиентские компоненты Oracle.|Да|Н/Д|Oracle 10g, 9, 8.1.7|Да|Да|  
|Реляционная база данных Teradata|[Teradata](#Teradata)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширяет поставщика данных .NET для Teradata от Teradata.<br /><br /> Требует поставщика данных .NET для Teradata от Teradata.<br /><br /> См. документацию Teradata по поддержке платформ.|Да|Н/Д|Teradata v14<br /><br /> Teradata v13<br /><br /> Teradata v12<br /><br /> Teradata v6.20|Да|Нет|  
|Реляционная база данных DB2|Имя специализированного зарегистрированного модуля обработки данных||2004 Host Integration (HI) Server<br /><br /> См. [документацию по Host Integration Server](https://msdn.microsoft.com/library/gg241192\(v=bts.10\).aspx).|Да|Недоступно|Недоступно|Да|Нет|  
|Обычный источник данных OLE DB|[OLEDB](#OLEDBStandard)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Любой источник данных, поддерживающий OLE DB.<br /><br /> См. документацию источника данных по поддержке платформ.|Да|Недоступно|Любой источник данных, поддерживающий OLE DB. См. [примечание](#OLEDBStandard).|Да|Недоступно|  
|Обычный источник данных ODBC|[интерфейс ODBC](#ODBCGeneric)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Любой источник данных, поддерживающий ODBC.<br /><br /> См. документацию источника данных по поддержке платформ.|Да|Недоступно|Любой источник данных, поддерживающий ODBC. См. [примечание](#ODBCGeneric).|Да|Да|  
  
 Сведения об использовании табличного источника данных, см. в разделе [подключения к данным, источники данных и строки подключения в службах Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Сведения об использовании внешних источников данных см. в разделе [Добавление данных из внешних источников данных (службы SSRS)](add-data-from-external-data-sources-ssrs.md).  
  
 Существует множество стандартных поставщиков данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сторонних производителей. Дополнительные сведения можно найти на сайтах или форумах сторонних производителей.  
  
 Для установки и регистрации специализированного модуля обработки данных или стандартного поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] понадобится справочная документация поставщика данных. Дополнительные сведения см. в статье [Регистрация стандартного поставщика данных .NET Framework (службы SSRS)](register-a-standard-net-framework-data-provider-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
## <a name="reporting-services-data-processing-extensions"></a>Модули обработки данных служб Reporting Services  
 Вместе со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и средой [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]автоматически устанавливаются следующие модули обработки данных. Дополнительные сведения и проверить установку, см. в разделе [файл конфигурации RSReportDesigner](../report-server/rsreportdesigner-configuration-file.md) и [файл конфигурации RSReportServer](../report-server/rsreportserver-config-configuration-file.md).  
  
> [!NOTE]  
>  Модуль обработки данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не поддерживается в настоящее время.  
  
 Дополнительные сведения о модулях обработки данных, поддерживаемых построителем отчетов, см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [документации по построителю отчетов](https://go.microsoft.com/fwlink/?LinkId=154494) на сайте msdn.microsoft.com.  
  
###  <a name="MicrosoftSQLServer"></a> Модуль обработки данных Microsoft SQL Server  
 Тип источника данных **Microsoft SQL Server** включает и расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)].  
  
 В среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]конструктор запросов, связанный с этим модулем данных, называется [Конструктором визуальных инструментов для создания баз данных](../../ssms/visual-db-tools/visual-database-tool-designers.md). Если конструктор запросов используется в графическом режиме, запрос анализируется и, возможно, переписывается. Текстовый конструктор запросов можно использовать при необходимости четкого управления синтаксисом [!INCLUDE[tsql](../../includes/tsql-md.md)] в запросе. Дополнительные сведения см. в разделах [Инструменты конструктора запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) и [Пользовательский интерфейс графического конструктора запросов](graphical-query-designer-user-interface.md).  
  
 Дополнительные сведения см. в разделе [Тип соединения SQL Server (службы SSRS)](sql-server-connection-type-ssrs.md).  
  
 В построителе отчетов конструктор запросов, связанный с этим модулем данных, называется конструктором реляционных запросов. Дополнительные сведения см. в разделе [Relational Query Designer User Interface](../relational-query-designer-user-interface.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="Azure"></a> Модуль обработки базы данных Azure SQL Windows  
 Тип источника данных **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]** включает и расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]графическим конструктором запросов, связанным с этим модулем обработки данных, является [пользовательский интерфейс конструктора реляционных запросов](../relational-query-designer-user-interface.md), а не [конструктор визуальных инструментов для баз данных](../../ssms/visual-db-tools/visual-database-tool-designers.md) , который используется с типом источника данных **Microsoft SQL Server** .  
  
 [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] автоматически распознает **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]** и **Microsoft SQL Server** источника данных и открывает графический конструктор, связанный с этим типом источника данных.  
  
 Если конструктор запросов используется в графическом режиме, запрос анализируется и, возможно, переписывается. Текстовый конструктор запросов также доступен для написания запросов. Текстовый конструктор запросов можно использовать при необходимости четкого управления синтаксисом [!INCLUDE[tsql](../../includes/tsql-md.md)] в запросе. Дополнительные сведения см. в разделе [Пользовательский интерфейс текстового конструктора запросов](../text-based-query-designer-user-interface.md).  
  
 Получение данных из [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется аналогично, однако существует ряд требований, относящихся только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Дополнительные сведения см. в разделе [Тип соединения SQL Azure (службы SSRS)](sql-azure-connection-type-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="PWD"></a> Модуль обработки данных параллельного хранилища данных Microsoft SQL Server  
 В среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]графическим конструктором запросов, связанным с этим модулем обработки данных, является [пользовательский интерфейс конструктора реляционных запросов](../relational-query-designer-user-interface.md), а не [конструктор визуальных инструментов для баз данных](../../ssms/visual-db-tools/visual-database-tool-designers.md) , который используется с типом источника данных **Microsoft SQL Server** .  
  
 [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] автоматически распознает **SQL Server Parallel Data Warehouse** и **Microsoft SQL Server** источника данных и открывает графический конструктор, связанный с этим типом источника данных.  
  
 Если конструктор запросов используется в графическом режиме, запрос анализируется и, возможно, переписывается. Текстовый конструктор запросов также доступен для написания запросов. Текстовый конструктор запросов можно использовать при необходимости четкого управления синтаксисом [!INCLUDE[tsql](../../includes/tsql-md.md)] в запросе. Дополнительные сведения см. в разделе [Пользовательский интерфейс текстового конструктора запросов](../text-based-query-designer-user-interface.md).  
  
 [!INCLUDE[ssDWCurrentFull](../../includes/ssdwcurrentfull-md.md)] не поддерживает использование хранимых процедур и функций, возвращающих табличные значения, в запросах. Дополнительные сведения см. в разделе [Тип соединения с параллельным хранилищем данных SQL Server (службы SSRS)](sql-server-parallel-data-warehouse-connection-type-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="AnalysisServices"></a> Модуль обработки данных служб Microsoft SQL Server Analysis Services  
 При выборе типа источника данных **Microsoft SQL Server Analysis Services**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и x64.  
  
 Поставщик данных использует объектную модель ADOMD.NET для создания запросов с помощью XML для аналитики (XMLA) версии 1.1. Результаты возвращаются в виде плоского набора строк. Дополнительные сведения см. в разделах [Тип соединения служб Analysis Services для запросов многомерных выражений (службы SSRS)](analysis-services-connection-type-for-mdx-ssrs.md), [Тип соединения служб Analysis Services для расширений интеллектуального анализа данных (службы SSRS)](analysis-services-connection-type-for-dmx-ssrs.md), [Пользовательский интерфейс конструктора запросов многомерных выражений служб Analysis Services](analysis-services-mdx-query-designer-user-interface.md) и [Пользовательский интерфейс конструктора DMX-запросов служб Analysis Services](analysis-services-dmx-query-designer-user-interface.md).  
  
 При соединении с источником данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] модуль обработки данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает параметры с несколькими значениями и сопоставляет свойства ячеек и элементов с расширенными свойствами, поддерживаемыми службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в разделе [Расширенные свойства поля для базы данных служб Analysis Services &#40;SSRS&#41;](extended-field-properties-for-an-analysis-services-database-ssrs.md).  
  
 Вы можете также создавать модели на основе источников данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
###  <a name="OLEDBAll"></a> OLE DB Data Processing Extension  
 Модуль обработки данных OLE DB требует выбора дополнительного уровня поставщика данных в зависимости от версии источника данных, который необходимо использовать в отчете. Если конкретный поставщик данных не выбран, предоставляется поставщик по умолчанию. Выберите конкретный поставщик данных в диалоговом окне **Свойства соединения** , вызвать который можно, нажав кнопку **Изменить** в диалоговых окнах [Источник данных](../data-source-properties-dialog-box-general.md) или [Общий источник данных](../shared-data-source-properties-dialog-box-general.md) .  
  
 Дополнительные сведения о соответствующем конструкторе запросов OLE DB см. в разделах [Инструменты конструктора запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) и [Пользовательский интерфейс графического конструктора запросов](graphical-query-designer-user-interface.md). Дополнительные сведения об определенной поддержке поставщиков OLE DB см. в статье [Конструктор Visual Studio .NET поддерживает отдельных поставщиков данных OLE DB](https://support.microsoft.com/default.aspx/kb/811241) базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
####  <a name="OLEDBSQL"></a> OLE DB для SQL Server  
 При выборе типа источника данных **OLE DB**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для OLE DB. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и x64.  
  
 Дополнительные сведения см. в разделе [Тип соединения OLE DB (службы SSRS)](ole-db-connection-type-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
####  <a name="OLEDBAS9"></a> OLE DB для служб Analysis Services 9.0  
 Для подключения к службам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]выберите поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 9.0выберите поставщик the data source type **OLE DB**, а затем выберите соответствующий по имени базовый поставщик данных. Такое сочетание модуля обработки данных и поставщика данных скомпилировано в собственном коде для платформ на базе x86 и x64.  
  
> [!NOTE]  
>  Этот модуль обработки данных не поддерживает агрегирование серверов, автоматическое сопоставление расширенных свойств полей и параметры запросов. Рекомендованным поставщиком данных для источника данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] являются службы **Microsoft SQL Server Analysis Services**.  
  
 Дополнительные сведения см. в разделе [Тип соединения OLE DB (службы SSRS)](ole-db-connection-type-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
#### <a name="ole-db-for-olap-70"></a>OLE DB для OLAP 7.0  
 Поставщик OLE DB для служб OLAP Services 7.0 не поддерживается.  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
####  <a name="OracleOLEDB"></a> OLE DB для Oracle  
 Модуль обработки данных OLE DB для Oracle не поддерживает следующие типы данных Oracle: BLOB, CLOB, NCLOB, BFILE, UROWID.  
  
 Поддерживаются безымянные параметры, зависящие от позиции. Именованные параметры этим модулем не поддерживаются. Для работы с именованными параметрами используйте модуль обработки данных [Oracle](#OracleClient) .  
  
 Дополнительные сведения о настройке Oracle в качестве источника данных см. в разделе [Как использовать службы Reporting Services для настройки источника данных Oracle и доступа к нему](https://support.microsoft.com/kb/834305). Сведения о дополнительной настройке разрешений см. в статье [Как добавить разрешения для субъекта безопасности NETWORK SERVICE](https://support.microsoft.com/kb/870668) базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
####  <a name="OLEDBStandard"></a> Стандартный поставщик данных OLE DB .NET Framework  
 Для получения данных из источника, поддерживающего поставщики данных OLE DB [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , используйте тип источника данных **OLE DB** и выберите поставщика данных по умолчанию или из списка установленных поставщиков данных в диалоговом окне **Строка соединения** .  
  
> [!NOTE]  
>  Несмотря на то, что поставщик данных может поддерживать предварительный просмотр отчета на системе клиента, создающего отчет, не все поставщики данных OLE DB поддерживают отчеты, опубликованные на сервере отчетов.  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="ODBC"></a> ODBC Data Processing Extension  
 При выборе типа источника данных **ODBC**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для ODBC. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)] . Этот модуль может быть использован для подключения к любому источнику данных, использующему поставщик ODBC, и получения данных из него.  
  
> [!NOTE]  
>  Несмотря на то, что поставщик данных может поддерживать предварительный просмотр отчета на системе клиента, создающего отчет, не все поставщики данных ODBC поддерживают отчеты, опубликованные на сервере отчетов.  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
####  <a name="ODBCGeneric"></a> Стандартный поставщик данных ODBC .NET Framework  
 Для получения данных из источника, поддерживающего поставщики данных ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , используйте тип источника данных **ODBC** и выберите поставщика данных по умолчанию или из списка установленных поставщиков данных в диалоговом окне **Строка соединения** .  
  
> [!NOTE]  
>  Несмотря на то, что поставщик данных может поддерживать предварительный просмотр отчета на системе клиента, создающего отчет, не все поставщики данных ODBC поддерживают отчеты, опубликованные на сервере отчетов.  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="OracleClient"></a> Модуль обработки данных Oracle  
 При выборе типа источника данных **Oracle**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для Oracle. **Oracle** источник данных включает и расширяет возможности <xref:System.Data.OracleClient> необходимые классы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Для получения данных отчета из базы данных Oracle администратор должен установить клиентские инструменты Oracle. Этот поставщик данных использует интерфейс Oracle Call Interface (OCI) выпуска Oracle 8i версии 3, поставляемого в составе клиентского программного обеспечения Oracle. Клиентское приложение должно иметь версию не ниже 8.1.7. Эти инструменты должны быть установлены на системе клиента, создающего отчеты, для предварительного просмотра отчетов и на сервере отчетов для просмотра опубликованных отчетов.  
  
 Этот модуль поддерживает именованные параметры. Oracle версии 9 или более поздней поддерживает параметры с несколькими значениями. Для работы с безымянными параметрами, зависящими от позиции, используйте модуль обработки данных OLE DB с поставщиком данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Oracle. Дополнительные сведения о настройке Oracle в качестве источника данных см. в разделе [Как использовать службы Reporting Services для настройки источника данных Oracle и доступа к нему](https://support.microsoft.com/kb/834305). Сведения о дополнительной настройке разрешений см. в статье [Как добавить разрешения для субъекта безопасности NETWORK SERVICE](https://support.microsoft.com/kb/870668) базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Можно получить данные из хранимых процедур с несколькими входными параметрами, но эти процедуры должны возвращать только один выходной курсор. Дополнительные сведения см. в разделе об Oracle статьи [Получение данных с помощью модуля DataReader](https://go.microsoft.com/fwlink/?LinkId=81758).  
  
 Дополнительные сведения см. в разделе [Тип соединения Oracle (службы SSRS)](oracle-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделах [Инструменты конструктора запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) и [Пользовательский интерфейс графического конструктора запросов](graphical-query-designer-user-interface.md).  
  
 Также можно создавать модели на основе базы данных Oracle.  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="Teradata"></a> Модуль обработки данных Teradata  
 При выборе типа источника данных **Teradata**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных .NET Framework для Teradata. Чтобы получить данные отчета из базы данных Teradata, системный администратор должен установить поставщика данных .NET Framework для Teradata на клиенте разработки отчетов для предварительного просмотра отчетов и на сервере отчетов для просмотра опубликованных отчетов.  
  
 Для проектов сервера отчетов не существует графического конструктора запросов для этого модуля. Для создания запросов используйте текстовый конструктор запросов.  
  
 В следующей таблице показаны поддерживаемые версии поставщика данных .NET Framework для Teradata для определения источника в определении отчета в [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]:  
  
|[!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] version|Версия базы данных Teradata|Поставщик данных .NET Framework для ODBC|  
|-----------------------------------|-------------------------------|-------------------------------------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|12.00|12.00|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|6.20|12.00|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|12.00|12.00.01|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|6.20|12.00.01|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|13.00|13.0.0.1|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|12.00|12.00.01|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|6.20|12.00.01|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|13.00|13.0.0.1|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|6.20|12.00.01|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|12.00|12.00.01|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|13.00|13.0.0.1|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|14.00|14.00.01|  
  
 Этот модуль поддерживает многозначные параметры. Макросы могут быть указаны в запросе с использованием команды EXECUTE в режиме запроса TEXT.  
  
 Дополнительные сведения см. в разделе [Тип соединения Teradata (службы SSRS)](teradata-connection-type-ssrs.md).  
  
 Также можно создавать модели на основе базы данных Teradata. Дополнительные сведения см. в следующем техническом документе на веб-сайте Teradata: [Службы Microsoft SQL Server 2012 Reporting Services и корпорация Teradata](http://www.teradata.com/white-papers/Microsoft-SQL-Server-2012-Reporting-Services-and-Teradata-Corporation/?type=WP).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="SharePointList"></a> Модуль обработки списка данных SharePoint  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки списка данных SharePoint служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , поэтому списки SharePoint могут быть использованы в качестве источника данных в отчете. Данные списка можно получить из следующих источников:  
  
-   [!INCLUDE[SPS2013](../../includes/sps2013-md.md)]  
  
-   [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] и [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]  
  
-   [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 и [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007  
  
 Существует три способа реализации поставщика данных списка SharePoint.  
  
1.  Из среды создания отчетов, такой как построитель отчетов или конструктор отчетов в среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]или сервера отчетов, настроенного для работы в собственном режиме, данные списка приходят из веб-службы Lists.asmx для сайта SharePoint.  
  
2.  На сервере отчетов, работающем в режиме интеграции с SharePoint, данные списка приходят либо из соответствующей веб-службы Lists.asmx, либо из программных вызовов SharePoint API. В этом режиме можно получить данные списка из фермы SharePoint.  
  
3.  Для [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] и [!INCLUDE[SPS2013](../../includes/sps2013-md.md)] надстройка служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для технологий [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint позволяет получить данные списка из веб-службы Lists.asmx для сайта SharePoint либо с сайта SharePoint, который является частью фермы SharePoint. Этот сценарий также известен как *локальный режим* , поскольку сервер отчетов для этого не требуется.  
  
 Указываемые учетные данные зависят от реализации, которую использует клиентское приложение. Дополнительные сведения см. в разделе [Тип подключения к списку SharePoint](sharepoint-list-connection-type-ssrs.md).  
  
###  <a name="XML"></a> Модуль обработки XML-данных  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки данных XML, что позволяет использовать их в отчете. Данные могут быть получены из XML-документа, веб-службы или из веб-приложения, доступ к которым осуществляется с помощью URL-адреса. Дополнительные сведения см. в разделе [Тип соединения XML (службы SSRS)](xml-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделе о текстовом конструкторе запросов статьи [Пользовательский интерфейс графического конструктора запросов](graphical-query-designer-user-interface.md). Примеры можно найти в разделах [Службы Reporting Services: использование источников XML-данных и источников данных веб-служб](https://go.microsoft.com/fwlink/?LinkId=81654).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="SapBINetWeaver"></a> Модуль обработки данных SAP NetWeaver Business Intelligence  
 Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки данных, позволяющий использовать в отчетах данные из источника данных [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].  
  
 Дополнительные сведения см. в разделе [Тип соединения SAP NetWeaver BI (службы SSRS)](sap-netweaver-bi-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделе [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md).  
  
 Дополнительные сведения о [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]см. в разделе [Использование служб SQL Server 2008 Reporting Services совместно с SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="Hyperion"></a> Модуль обработки данных Hyperion Essbase Business Intelligence  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки данных, позволяющий использовать в отчетах данные из источника данных [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
 Дополнительные сведения см. в разделе [Тип соединения Hyperion Essbase (службы SSRS)](hyperion-essbase-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделе [Hyperion Essbase Query Designer User Interface](hyperion-essbase-query-designer-user-interface.md).  
  
 Дополнительные сведения об [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]см. в разделе [Использование служб SQL Server 2005 Reporting Services совместно с Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
## <a name="see-also"></a>См. также  
 [Подключения к данным, источники данных и строки подключения в службах Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Добавление данных в отчет &#40;построитель отчетов и службы SSRS&#41;](report-datasets-ssrs.md)  
  
  
