---
title: Источники данных, поддерживаемые службами Reporting Services | Документация Майкрософт
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
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
ms.openlocfilehash: e37b386b0dd8fd5a596096b8f56e87db1a0fa1e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77078119"
---
# <a name="data-sources-supported-by-reporting-services-ssrs"></a>Источники данных, поддерживаемые службами Reporting Services (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] получают через модульный и расширяемый уровень данных, где работают модули обработки данных. Для получения данных отчета из источника данных необходимо выбрать модуль обработки данных, поддерживающий как тип источника данных, так и версию программного обеспечения источника данных и его платформу (32-разрядная или 64-разрядная [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]).  
  
 При развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]набор модулей обработки данных, предоставляющих доступ к различным типам источников данных, автоматически устанавливается и регистрируется как в системе создающего отчеты клиента, так и на сервере отчетов. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливают следующие типы источников данных.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для многомерных выражений, расширений интеллектуального анализа данных, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] и табличных моделей;  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]  
  
-   Oracle;  
  
-   SAP BW 
  
-   [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint  
  
-   Teradata  
  
-   OLE DB  
  
-   ODBC  
  
-   XML  
  
 Кроме того, системный администратор может установить и зарегистрировать пользовательские модули обработки данных и стандартные поставщики данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Для обработки и просмотра отчета модули обработки данных и поставщики данных должны быть установлены и зарегистрированы на сервере отчетов. Для предварительного просмотра отчета их также необходимо установить и зарегистрировать на клиенте, где производится создание отчетов. Модули обработки данных и поставщики данных должны быть скомпилированы в собственном коде для той платформы, на которую устанавливаются. Если развертывание источника данных производится программными средствами с помощью веб-службы SOAP, необходимо определить модуль источника данных. Используйте значения модуля обработки данных из файла **RSReportDesigner.config** . По умолчанию файл находится в следующей папке:  
  
```  
<drive letter>\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
```  
  
 Например, модуль обработки данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] представляет собой OLEDB-MD.  
  
 Многие стандартные поставщики данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сторонних производителей можно скачать в [Центре загрузки Майкрософт](https://www.microsoft.com/download/default.aspx) и на сайтах сторонних производителей. Сведения о поставщиках данных сторонних производителей можно найти также на общедоступном форуме по службам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Стандартные поставщики данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] необязательно поддерживают все функции, предоставляемые модулями обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Кроме того, некоторые поставщики данных OLE DB и драйверы ODBC могут быть использованы для создания и предварительного просмотра отчетов, но не поддерживают отчеты, опубликованные на сервере отчетов. Например, поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet не поддерживается на сервере отчетов. Дополнительные сведения см. в разделе [Модули обработки данных и поставщики данных .NET Framework (службы SSRS)](../../reporting-services/report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md).  
  
 Дополнительные сведения о развертывании специализированных модулей обработки данных см. в разделе [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md). Дополнительные сведения о стандартных поставщиках данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе по пространству имен <xref:System.Data> .   
  
## <a name="platform-support-for-report-data-sources"></a>Поддержка платформ источников данных отчета  
 Источники данных, которые вы можете использовать в развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , различаются в зависимости от выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и платформы. Дополнительные сведения о компонентах см. в статье [Компоненты Reporting Services, поддерживаемые выпусками SQL Server](../../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md). Приведенная далее в разделе таблица содержит сведения о поддерживаемых источниках данных в зависимости от версии и платформы.  
  
 Требования к платформам для источников данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] различаются для системы клиента, создающего отчеты, и сервера отчетов.  
  
### <a name="on-the-report-authoring-client"></a>На системе клиента, создающего отчеты  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] — это 32-разрядное приложение. [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] не поддерживается на платформе Itanium. На платформе x64 для изменения и предварительного просмотра отчетов в конструкторе отчетов необходимо наличие 32-разрядных версий поставщиков данных, установленных в каталоге платформы (x86).  
  
### <a name="on-the-report-server"></a>На сервере отчетов  
 При развертывании отчета в 64-разрядной версии сервера отчетов на нем должны быть установлены 64-разрядные версии поставщиков данных, скомпилированные в машинном коде. Упаковка 32-разрядной версии поставщика данных в 64-разрядные интерфейсы не поддерживается. Дополнительные сведения см. в документации по поставщику данных.  
  
## <a name="supported-data-sources"></a>Поддерживаемые источники данных  
 В следующей таблице перечислены поставщики данных и модули обработки данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] , которые могут использоваться для получения данных для наборов данных и моделей отчетов. Дополнительные сведения о модуле обработки данных или поставщике данных можно получить, перейдя по ссылке во втором столбце. Столбцы таблицы содержат следующие сведения:  
  
-   Источник данных отчета. Тип данных, к которым осуществляется доступ. Например, реляционная база данных, многомерная база данных, неструктурированный файл или XML-файл. Этот столбец отвечает на вопрос: "Данные каких типов может использовать [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в отчете служб?"  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Тип источника данных. Один из типов источников данных, содержащихся в раскрывающемся списке при определении источника данных в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Этот список содержит установленные и зарегистрированные модули обработки данных и поставщики данных. Этот столбец отвечает на вопрос: "Какие типы источников данных можно выбрать из раскрывающегося списка при создании источника данных отчета?"  
  
-   Имя модуля обработки данных или поставщика данных. Модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или другой поставщик данных, отвечающий выбранному типу источника данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Этот столбец отвечает на вопрос: "Какой модуль обработки данных или поставщик данных используется при выборе данного типа источника данных?"  
  
-   Версия базового поставщика данных (необязательно). Некоторые типы источников данных поддерживают более одного поставщика данных. Это могут быть как разные версии одного и того же поставщика, так и разные реализации этого типа поставщика данных от сторонних производителей. Имя этого поставщика зачастую появляется в строке соединения после настройки источника данных. Этот столбец отвечает на вопрос: "Какой поставщик данных можно выбрать в диалоговом окне **Свойства соединения** после выбора типа источника данных?"  
  
-   Платформа *\<источника данных*: Платформа источника данных, поддерживаемая модулем обработки данных или поставщиком данных для данного целевого источника данных. Этот столбец отвечает на вопрос: "Может ли этот модуль обработки данных или поставщик данных получать данные из источника данных на платформе этого типа?"  
  
-   Версия источника данных. Версия целевого источника данных, поддерживаемая модулем обработки данных или поставщиком данных. Этот столбец отвечает на вопрос: "Может ли этот модуль обработки данных или поставщик данных получать данные из этой версии источника данных?"  
  
-   Платформа *\<RS*: Платформы сервера отчетов и системы клиента, создающего отчеты, на которых можно установить специализированный модуль обработки данных или поставщик данных. Встроенные модули обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] всегда устанавливаются вместе со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Специализированный модуль обработки данных или поставщик данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] должен быть скомпилирован в виде собственного кода для конкретной платформы. Этот столбец отвечает на вопрос: "Можно ли установить на данном типе платформы этот модуль обработки данных или поставщик данных?"  
  
###  <a name="DataSourcesTable"></a> Типы источников данных  
  
|Источник<br /><br /> данных отчета|Тип источника данных служб Reporting Services|Имя модуля обработки данных или поставщика данных|Версия базового поставщика данных<br /><br /> (необязательно)|Данные<br /><br /> Источник<br /><br /> на платформе x86|Данные<br /><br /> Источник<br /><br /> на платформе x64|Версия источника данных|Сервер отчетов<br /><br /> на платформе x86|Сервер отчетов<br /><br /> на платформе x64|  
|-------------------------------|-----------------------------------------|------------------------------------------------------|-------------------------------------------------------|--------------------------------------|--------------------------------------|----------------------------|-------------------------|-------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реляционная база данных|[Microsoft SQL Server](#MicrosoftSQLServer)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.SqlClient|Да|Да|SQL Server 2008 и более поздней версии.|Да|Да|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реляционная база данных|OLEDB|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OledbClient|Да|Да|SQL Server 2008 и более поздней версии.|Да|Да|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реляционная база данных|[ODBC](#ODBC)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OdbcClient|Да|Да|SQL Server 2008 и более поздней версии.|Да|Да|  
|[!INCLUDE[ssSDS](../../includes/sssds-md.md)]|[База данных SQL Microsoft Azure](#Azure)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.SqlClient|Недоступно|Недоступно|[!INCLUDE[ssSDS](../../includes/sssds-md.md)]|Да|Да|
|Хранилище данных SQL|[База данных SQL Microsoft Azure](#Azure)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.SqlClient|Недоступно|Недоступно|Хранилище данных SQL|Да|Да| 
|[!INCLUDE[ssDW](../../includes/ssdw-md.md)] (модуль)|[Параллельные хранилища данных Microsoft](#PWD)|Нерекомендуемый модуль обработки данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Недоступно|Недоступно|Недоступно|[!INCLUDE[ssDWfull](../../includes/ssdwfull-md.md)]|Нет|Нет|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (многомерная база данных)|[Службы Microsoft SQL Server Analysis Services](#AnalysisServices)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Использует ADOMD.NET|Да|Да|SQL Server 2008 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и более поздние версии|Да|Да|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (многомерная база данных)|OLEDB|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширение класса System.Data.OledbClient<br /><br /> Версия 10.0|Да|Да|SQL Server 2008 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Да|Да|   
|Списки SharePoint|[Список Microsoft SharePoint](#SharePointList)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Возвращает данные из Lists.asmx или API-интерфейсов объектной модели SharePoint.<br /><br /> См. [примечание](#SharePointList).|Нет|Да|Продукты SharePoint 2013 и более поздних версий|Да|Да|   
|XML|[XML](#XML)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Источники XML-данных не зависят от платформы.|Недоступно|Недоступно|[!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)] или документы|Да|Да|  
|Модель сервера отчетов|Модель отчета|Нерекомендуемый модуль обработки данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для опубликованного SMDL-файла|Источники данных для модели используют встроенные модули обработки данных.<br /><br /> Для моделей на основе Oracle требуются клиентские компоненты Oracle.<br /><br /> Для моделей на основе Teradata требуется поставщик данных .NET для Teradata от Teradata.<br /><br /> См. документацию Teradata по поддержке платформ.|Недоступно|Недоступно|Источники создания моделей:[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии<br /><br /> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<br /><br /> Oracle 9.2.0.3 или более поздней версии<br /><br /> Teradata V14, v13, v12 и v6.2|Нет|Нет|  
|Многомерная база данных SAP|SAP BW|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|См. документацию SAP по поддержке платформ.|Недоступно|Недоступно|SAP BW 7.0–7.5|Да|Недоступно|  
|[!INCLUDE[extEssbase](../../includes/extessbase-md.md)]|[Hyperion Essbase](#Hyperion)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|См. документацию Hyperion по поддержке платформ.|Да|Недоступно|[!INCLUDE[extEssbase](../../includes/extessbase-md.md)] 9.3.1|Да|Недоступно|  
|Реляционная база данных Oracle|[Oracle](#OracleClient)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Необходимы клиентские компоненты Oracle 12c или более поздней версии.|Да|Недоступно|Oracle 11g, 11g R2, 12c|Да|Да|  
|Teradata |[Teradata](#Teradata)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Расширяет поставщика данных .NET для Teradata от Teradata.<br /><br /> Требует поставщика данных .NET для Teradata от Teradata.<br /><br /> См. документацию Teradata по поддержке платформ.|Да|Недоступно|Teradata v15<br /><br />Teradata v14<br /><br /> Teradata v13|Да|Нет|  
|Реляционная база данных DB2|Имя специализированного зарегистрированного модуля обработки данных||2004 Host Integration (HI) Server<br /><br /> |Да|Недоступно|Недоступно|Да|Нет|  
|Обычный источник данных OLE DB|OLEDB|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Любой источник данных, поддерживающий OLE DB.<br /><br /> См. документацию источника данных по поддержке платформ.|Да|Недоступно|Любой источник данных, поддерживающий OLE DB. См. [примечание](#OLEDBStandard).|Да|Недоступно|  
|Обычный источник данных ODBC|[ODBC](#ODBCGeneric)|Встроенный модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Любой источник данных, поддерживающий ODBC.<br /><br /> См. документацию источника данных по поддержке платформ.|Да|Недоступно|Любой источник данных, поддерживающий ODBC. См. [примечание](#ODBCGeneric).|Да|Да|  
  
 Сведения об использовании внешних источников данных см. в разделе [Добавление данных из внешних источников данных (службы SSRS)](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md).  
  
 Существует множество стандартных поставщиков данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сторонних производителей. Дополнительные сведения можно найти на сайтах или форумах сторонних производителей.  
  
 Для установки и регистрации специализированного модуля обработки данных или стандартного поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] понадобится справочная документация поставщика данных. Дополнительные сведения см. в статье [Регистрация стандартного поставщика данных .NET Framework (службы SSRS)](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
## <a name="reporting-services-data-processing-extensions"></a>Модули обработки данных служб Reporting Services  
 Вместе со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и средой [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]автоматически устанавливаются следующие модули обработки данных. Дополнительные сведения, а также сведения по проверке установки см. в разделах [Файл конфигурации RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md) и [Файл конфигурации RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).  
  
> [!NOTE]
>  Модуль обработки данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не поддерживается в настоящее время.  
  
 Дополнительные сведения о модулях обработки данных, поддерживаемых построителем отчетов, см. в статье [Create data connection strings - Report Builder & SSRS](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) (Создание строки подключения к данным в построителе отчетов и SSRS).
  
###  <a name="MicrosoftSQLServer"></a> Модуль обработки данных Microsoft SQL Server  
 Тип источника данных **Microsoft SQL Server** включает и расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)].  
  
 В среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] конструктор запросов, связанный с этим модулем данных, называется визуальным конструктором инструментов для создания баз данных. Если конструктор запросов используется в графическом режиме, запрос анализируется и, возможно, переписывается. Текстовый конструктор запросов можно использовать при необходимости четкого управления синтаксисом [!INCLUDE[tsql](../../includes/tsql-md.md)] в запросе. Дополнительные сведения см. в статье [Graphical Query Designer User Interface](../../reporting-services/report-data/graphical-query-designer-user-interface.md).  
  
 Дополнительные сведения см. в разделе [Тип соединения SQL Server (службы SSRS)](../../reporting-services/report-data/sql-server-connection-type-ssrs.md).  
  
 В построителе отчетов конструктор запросов, связанный с этим модулем данных, называется конструктором реляционных запросов. 
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="Azure"></a> Модуль обработки для базы данных SQL Microsoft Azure  
 Тип источника данных **Microsoft Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** включает и расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 В среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] графическим конструктором запросов, связанным с этим модулем обработки данных, является конструктор реляционных запросов, а не визуальный конструктор инструментов для создания баз данных, который используется с типом источников данных **Microsoft SQL Server**.  
  
 Среда [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] автоматически различает типы источников данных **Microsoft Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** и **Microsoft SQL Server** и открывает графический конструктор запросов, связанный с типом источника данных.  
  
 Если конструктор запросов используется в графическом режиме, запрос анализируется и, возможно, переписывается. Текстовый конструктор запросов также доступен для написания запросов. Текстовый конструктор запросов можно использовать при необходимости четкого управления синтаксисом [!INCLUDE[tsql](../../includes/tsql-md.md)] в запросе.   
  
 Получение данных из [!INCLUDE[ssSDS](../../includes/sssds-md.md)], хранилища данных SQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется аналогично, однако существует ряд требований, относящихся только к [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Дополнительные сведения см. в разделе [Тип соединения SQL Azure (службы SSRS)](../../reporting-services/report-data/sql-azure-connection-type-ssrs.md).  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="PWD"></a> Модуль обработки данных параллельного хранилища данных Microsoft SQL Server  
Этот источник данных является нерекомендуемым. Для подключения к Microsoft Analytics Platform (APS) используйте тип источника данных SQL Server.
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="AnalysisServices"></a> Модуль обработки данных служб Microsoft SQL Server Analysis Services  
 При выборе типа источника данных **Microsoft SQL Server Analysis Services** выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], который расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и x64.  
  
 Поставщик данных использует объектную модель ADOMD.NET для создания запросов с помощью XML для аналитики (XMLA) версии 1.1. Результаты возвращаются в виде плоского набора строк. Дополнительные сведения см. в разделах [Тип соединения служб Analysis Services для запросов многомерных выражений (службы SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md), [Тип соединения служб Analysis Services для расширений интеллектуального анализа данных (службы SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md), [Пользовательский интерфейс конструктора запросов многомерных выражений служб Analysis Services](../../reporting-services/report-data/analysis-services-mdx-query-designer-user-interface.md) и [Пользовательский интерфейс конструктора DMX-запросов служб Analysis Services](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md).  
  
 При соединении с источником данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] модуль обработки данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает параметры с несколькими значениями и сопоставляет свойства ячеек и элементов с расширенными свойствами, поддерживаемыми [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в разделе [Расширенные свойства поля для базы данных служб Analysis Services &#40;SSRS&#41;](../../reporting-services/report-data/extended-field-properties-for-an-analysis-services-database-ssrs.md).  
  
 Вы можете также создавать модели на основе источников данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
###  <a name="OLEDBAll"></a> OLE DB Data Processing Extension  
 Модуль обработки данных OLE DB требует выбора дополнительного уровня поставщика данных в зависимости от версии источника данных, который необходимо использовать в отчете. Если конкретный поставщик данных не выбран, предоставляется поставщик по умолчанию. Выберите конкретный поставщик данных в диалоговом окне **Свойства соединения**, открыть которое можно, нажав кнопку **Изменить** в диалоговых окнах "Источник данных" или "Общий источник данных".  
  
 Дополнительные сведения о соответствующем конструкторе запросов OLE DB см. в разделах [Пользовательский интерфейс графического конструктора запросов](../../reporting-services/report-data/graphical-query-designer-user-interface.md). Дополнительные сведения об определенной поддержке поставщиков OLE DB см. в статье [Конструктор Visual Studio .NET поддерживает отдельных поставщиков данных OLE DB](https://support.microsoft.com/default.aspx/kb/811241) базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
####  <a name="OLEDBSQL"></a> OLE DB для SQL Server  
 При выборе типа источника данных **OLE DB**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для OLE DB. Этот модуль обработки данных скомпилирован в собственном коде для платформ на базе x86 и x64.  
  
 Дополнительные сведения см. в разделе [Тип соединения OLE DB (службы SSRS)](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  
  
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
 При выборе типа источника данных **Oracle** вы выбираете модуль обработки данных [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], который использует поставщик данных Oracle напрямую, а не через System.Data.OracleClient. Для получения данных отчета из базы данных Oracle администратор должен установить клиентские инструменты Oracle. Клиентское приложение должно иметь версию не ниже 11g. Эти инструменты должны быть установлены на системе клиента, создающего отчеты, для предварительного просмотра отчетов и на сервере отчетов для просмотра опубликованных отчетов.  
 
Чтобы установить инструменты клиента Oracle, можно выполнить указанные ниже действия.
 
1.  Перейдите на [сайт загрузки Oracle](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html).
2.  Скачайте ODAC 12c 4 выпуска (12.1.0.2.4) для Windows (64-разрядная версия для сервера, 32-разрядная версия для инструментов).
3.  Установите поставщик данных Oracle для .NET 4.
  
 Этот модуль поддерживает именованные параметры. Oracle версии 11g или более поздней поддерживает параметры с несколькими значениями. Для работы с безымянными параметрами, зависящими от позиции, используйте модуль обработки данных OLE DB с поставщиком данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Oracle. Дополнительные сведения о настройке Oracle в качестве источника данных см. в разделе [Как использовать службы Reporting Services для настройки источника данных Oracle и доступа к нему](https://support.microsoft.com/kb/834305). Сведения о дополнительной настройке разрешений см. в статье [Как добавить разрешения для субъекта безопасности NETWORK SERVICE](https://support.microsoft.com/kb/870668) базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Можно получить данные из хранимых процедур с несколькими входными параметрами, но эти процедуры должны возвращать только один выходной курсор. Дополнительные сведения см. в разделе [Returning results with Oracle REF CURSORs](https://docs.microsoft.com/dotnet/framework/data/adonet/retrieving-data-using-a-datareader#returning-results-with-oracle-ref-cursors) (Возвращение результатов при помощи Oracle REF CURSOR) в статье "Retrieve data using a DataReader" (Получение данных с помощью DataReader).
  
 Дополнительные сведения см. в разделе [Тип соединения Oracle (службы SSRS)](../../reporting-services/report-data/oracle-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделах [Пользовательский интерфейс графического конструктора запросов](../../reporting-services/report-data/graphical-query-designer-user-interface.md).  
  
 Также можно создавать модели на основе базы данных Oracle.  
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="Teradata"></a> Модуль обработки данных Teradata  
 При выборе типа источника данных **Teradata**выбирается модуль обработки данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который расширяет возможности поставщика данных .NET Framework для Teradata. Чтобы получить данные отчета от Teradata, системный администратор должен установить поставщика данных .NET Framework для Teradata на клиенте разработки отчетов для предварительного просмотра отчетов и на сервере отчетов для просмотра опубликованных отчетов.  
  
 Для проектов сервера отчетов не существует графического конструктора запросов для этого модуля. Для создания запросов используйте текстовый конструктор запросов.  
  
 В следующей таблице показаны поддерживаемые версии поставщика данных .NET Framework для Teradata для определения источника в определении отчета в [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]:  
  
|[!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] version|Версия Teradata|Поставщик данных .NET Framework для ODBC|  
|-----------------------------------|-------------------------------|-------------------------------------------------------|    
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|12,00|12.00.01|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|6.20|12.00.01|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|13.00|13.0.0.1|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|12,00|12.00.01|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|6.20|12.00.01|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|13.00|13.0.0.1|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|6.20|12.00.01|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|12,00|12.00.01|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|13.00|13.0.0.1|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|14.00|14.00.01| 
|SQL Server 2016|13.00|13.0.0.1|  
|SQL Server 2016|14.00|14.00.01|
|SQL Server 2016|15,00|15.00.01| 
  
 Этот модуль поддерживает многозначные параметры. Макросы могут быть указаны в запросе с использованием команды EXECUTE в режиме запроса TEXT.  
  
 Дополнительные сведения см. в разделе [Тип соединения Teradata (службы SSRS)](../../reporting-services/report-data/teradata-connection-type-ssrs.md).  
 
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="SharePointList"></a> Модуль обработки списка данных SharePoint  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включает модуль обработки списка данных SharePoint служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], поэтому списки SharePoint могут быть использованы в качестве источника данных в отчете. Данные списка можно получить из следующих источников:  
  
-   SharePoint Server 2016  

-   [!INCLUDE[SPS2013](../../includes/sps2013-md.md)]  
  
 Существует три способа реализации поставщика данных списка SharePoint.  
  
1.  Из среды создания отчетов, такой как построитель отчетов или конструктор отчетов в среде [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)]или сервера отчетов, настроенного для работы в собственном режиме, данные списка приходят из веб-службы Lists.asmx для сайта SharePoint.  
  
2.  На сервере отчетов, работающем в режиме интеграции с SharePoint, данные списка приходят либо из соответствующей веб-службы Lists.asmx, либо из программных вызовов SharePoint API. В этом режиме можно получить данные списка из фермы SharePoint.  
  
3.  Для [!INCLUDE[SPS2013](../../includes/sps2013-md.md)] и SharePoint Server 2016 надстройка [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для технологий [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint позволяет получать данные списка из веб-службы Lists.asmx для сайта SharePoint либо с сайта SharePoint, который является частью фермы SharePoint. Этот сценарий также известен как *локальный режим* , поскольку сервер отчетов для этого не требуется.  
  
 Указываемые учетные данные зависят от реализации, которую использует клиентское приложение. Дополнительные сведения см. в разделе [Тип подключения к списку SharePoint](../../reporting-services/report-data/sharepoint-list-connection-type-ssrs.md).  
  
###  <a name="XML"></a> Модуль обработки XML-данных  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки данных XML, что позволяет использовать их в отчете. Данные могут быть получены из XML-документа, веб-службы или из веб-приложения, доступ к которым осуществляется с помощью URL-адреса. Дополнительные сведения см. в разделе [Тип соединения XML (службы SSRS)](../../reporting-services/report-data/xml-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделе о текстовом конструкторе запросов статьи [Пользовательский интерфейс графического конструктора запросов](../../reporting-services/report-data/graphical-query-designer-user-interface.md).
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="SAPBW"></a> Модуль обработки данных SAP BW  
 Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки данных, позволяющий использовать в отчетах данные из источника данных SAP BW.
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
###  <a name="Hyperion"></a> Модуль обработки данных Hyperion Essbase Business Intelligence  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль обработки данных, позволяющий использовать в отчетах данные из источника данных [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
 Дополнительные сведения см. в разделе [Тип соединения Hyperion Essbase (службы SSRS)](../../reporting-services/report-data/hyperion-essbase-connection-type-ssrs.md). Дополнительные сведения о соответствующем конструкторе запросов см. в разделе [Hyperion Essbase Query Designer User Interface](../../reporting-services/report-data/hyperion-essbase-query-designer-user-interface.md).  
  
 Дополнительные сведения о [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]: [Использование служб SQL Server Reporting Services совместно с Hyperion Essbase](../../reporting-services/report-data/hyperion-essbase-query-designer-user-interface.md). 
  
 [Назад к таблице источников данных](#DataSourcesTable)  
  
## <a name="see-also"></a>См. также:  
 [Create data connection strings — Report Builder & SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  (Создание строк подключения к данным (построитель отчетов и службы SSRS))  
 [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
  
  
