---
title: Доступ к данным многомерной модели (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, data access interfaces
- objects [Analysis Services], data access interfaces
- Analysis Services data access interfaces
- data retrieval [Analysis Services]
- retrieving data
- metadata [Analysis Services]
- data access interfaces [Analysis Services]
- manipulating objects [Analysis Services]
- Analysis Services data access interfaces, about data access interfaces
ms.assetid: 46388efb-3c78-47a2-b5c9-5a69ff394d03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cf03599736be8dbec6666c6977543279607bbdc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203724"
---
# <a name="multidimensional-model-data-access-analysis-services---multidimensional-data"></a>Доступ к данным многомерной модели (службы Analysis Services — многомерные данные)
  Сведения в этом разделе помогут ознакомиться со способами доступа к многомерным данным служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью программных методов доступа, скриптов или клиентских приложений, включающих встроенную поддержку соединения с сервером служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в сети.  
  
 Этот раздел состоит из следующих подразделов.  
  
 [Клиентские приложения](#bkmk_clientapps)  
  
 [Языки запросов](#bkmk_querylang)  
  
 [Программные интерфейсы](#bkmk_api)  
  
##  <a name="bkmk_clientapps"></a> Клиентские приложения  
 Хотя службы Analysis Services предоставляют интерфейсы, позволяющие создавать или интегрировать многомерные базы данных программными средствами, более широко распространен подход, при котором используются существующие клиентские приложения Майкрософт и других поставщиков данных со встроенными средствами доступа к данным служб Analysis Services.  
  
 Следующие клиентские приложения Майкрософт поддерживают собственные соединения с многомерными данными.  
  
### <a name="excel"></a>Excel  
 Многомерные данные служб Analysis Services часто представляются с помощью сводных таблиц и элементов управления сводными таблицами в книгах Excel. Сводные таблицы подходят для работы с многомерными данными, потому что иерархии, статистические выражения и механизмы навигации модели хорошо сочетаются с функциями сводных данных в сводных таблицах. Поставщик данных OLE DB служб Analysis Services входит в состав установки Microsoft Excel, что упрощает настройку соединений с данными. Дополнительные сведения см. в разделе [Подключение к службам SQL Server Analysis Services или импорт данных из них](http://go.microsoft.com/fwlink/?linkID=215150).  
  
### <a name="reporting-services-reports"></a>Reporting Services, отчеты служб  
 Для создания отчетов, использующих базы данных служб Analysis Services, которые содержат аналитические данные, можно использовать построитель отчетов или конструктор отчетов. И построитель отчетов, и конструктор отчетов содержат конструктор запросов многомерных выражений, который можно использовать для ввода или конструирования инструкций многомерных выражений, извлекающих данные из доступного источника данных. Дополнительные сведения см. в разделах [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md), [Тип соединения служб Analysis Services для многомерных выражений (службы SSRS)](../../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md).  
  
### <a name="performancepoint-dashboards"></a>Панели мониторинга PerformancePoint  
 Панели мониторинга PerformancePoint используются для создания в SharePoint оценочных листов, в которых показатели бизнеса сравниваются со стандартными величинами. PerformancePoint включает поддержку соединений с многими мерными данными служб Analysis Services. Дополнительные сведения см. в разделе [Создание подключений к данным служб Analysis Services (службы PerformancePoint)](http://go.microsoft.com/fwlink/?linkid=232471).  
  
### <a name="sql-server-data-tools"></a>SQL Server Data Tools (SSDT)  
 Конструкторы моделей и отчетов используют средства SQL Server Data Tools для построения решений, которые включают многомерные модели. При развертывании решения в экземпляре служб Analysis Services создается база данных, к которой в дальнейшем производятся подключения из Excel, служб Reporting Services и других клиентских приложений бизнес-аналитики.  
  
 Средства SQL Server Data Tools основаны на оболочке Visual Studio, и для хранения и упорядочивания моделей в них используются проекты. Дополнительные сведения см. в разделе [Создание многомерных моделей с помощью SQL Server Data Tools (SSDT)](../creating-multidimensional-models-using-sql-server-data-tools-ssdt.md).  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Для администраторов баз данных среда SQL Server Management Studio служит интегрированной средой управления экземплярами SQL Server, в том числе и экземплярами служб Analysis Services и многомерными базами данных. Дополнительные сведения см. в разделах [Среда SQL Server Management Studio](../../../ssms/sql-server-management-studio-ssms.md) и [Подключение к службам Analysis Services](../../instances/connect-to-analysis-services.md).  
  
##  <a name="bkmk_querylang"></a> Языки запросов  
 Язык многомерных выражений (MDX) является отраслевым стандартом языка запросов и вычислений, используемым при извлечении данных из баз данных OLAP. В службах Analysis Services язык многомерных выражений (MDX) — это язык запросов, используемый для извлечения данных, но также поддерживающий определение данных и изменение данных. Редакторы многомерных выражений встроены в среду SQL Server Management Studio, в службы Reporting Services и в средства SQL Server Data Tools. Редакторы многомерных выражений можно использовать для создания нерегламентированных запросов или скриптов, допускающих многократное использование, если операцию над данными необходимо повторять.  
  
 Некоторые инструменты и приложения, например Microsoft Excel, используют конструкции многомерных выражений во внутренних механизмах для выполнения запросов к источникам данных служб Analysis Services. Многомерные выражения также можно использовать программным образом, включая их в запросы XMLA Execute.  
  
 Дополнительные сведения о многомерных выражениях см. по следующим ссылкам.  
  
 [Запрос многомерных данных с помощью многомерных выражений](querying-multidimensional-data-with-mdx.md)  
  
 [Основные понятия многомерных выражений &#40;служб Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)  
  
 [Основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
 [Основные принципы создания скриптов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
##  <a name="bkmk_api"></a> Программные интерфейсы  
 При разработке пользовательского приложения, использующего многомерные данные, скорее всего, будет использоваться один из следующих способов доступа к данным.  
  
-   **XML для аналитики**. Используйте XML для аналитики, когда требуется обеспечить совместимость с широким рядом различных операционных систем и протоколов. XML для аналитики обеспечивает максимальную гибкость, но часто за счет снижения производительности и усложнения программирования.  
  
-   **Клиентские библиотеки**. Используйте клиентские библиотеки служб Analysis Services, такие как ADOMD.NET, AMO и OLE DB, при необходимости получить программный доступ к данным из клиентских приложений, работающих под управлением операционной системы Microsoft Windows. Клиентские библиотеки помещают XML для аналитики в объектную модель и реализуют оптимизации, которые повышают производительность.  
  
     Клиентские библиотеки ADOMD.NET и AMO предназначены для приложений, написанных на управляемом коде. Используйте OLE DB для служб Analysis Services, если приложение написано на машинном коде.  
  
 В следующих таблицах содержатся дополнительные сведения и ссылки по клиентским библиотекам, используемым для соединения со службами Analysis Services из пользовательских приложений.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|Управляющие объекты служб Analysis Services (AMO)|Объекты AMO — это основная объектная модель для администрирования экземпляров служб Analysis Services и многомерных баз данных из кода. Например, среда SQL Server Management Studio использует объекты AMO для поддержки администрирования серверов и баз данных. Дополнительные сведения см. в разделе [Разработка объектов управления аналитикой (объекты AMO)](../analysis-management-objects/developing-with-analysis-management-objects-amo.md).|  
|ADOMD.NET|ADOMD.NET служит основной объектной моделью для создания многомерных данных и доступа к ним в пользовательских приложениях. Для получения сведений служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью стандартных интерфейсов доступа к данным платформы Microsoft .NET в управляемом пользовательском приложении можно использовать ADOMD.NET. Дополнительные сведения см. в разделах [Разработка с использованием ADOMD.NET](../adomd-net/developing-with-adomd-net.md) и [Программирование клиента ADOMD.NET](../../multidimensional-models-adomd-net-client/adomd-net-client-programming.md).|  
|Поставщик OLE DB служб Analysis Services (MSOLAP.dll)|Для доступа к службам [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] из неуправляемого API-интерфейса программными средствами можно использовать собственный поставщик данных OLE DB. Дополнительные сведения см. в разделе [Поставщик OLE DB служб Analysis Services (службы Analysis Services — многомерные данные)](../../dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md).|  
|Наборы строк схемы|Таблицы наборов строк схемы — это структуры данных, содержащие описательные сведения о развернутой на сервере многомерной модели, а также о выполняющихся на сервере в настоящий момент действиях. Программист может выполнять запросы к таблицам наборов строк схемы из клиентских приложений, чтобы просматривать хранящиеся на экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] метаданные, а также для получения с него вспомогательной информации и данных отслеживания. Наборы строк схемы можно использовать со следующими программными интерфейсами: OLE DB, OLE DB для служб Analysis Services, OLE DB для интеллектуального анализа данных и XML для аналитики. Дополнительные сведения см. в разделе [Наборы строк схемы служб Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md).<br /><br /> В следующем списке описывается несколько подходов к использованию наборов строк схемы:<br /><br /> Выполнение запросов к динамическим административным представлениям из среды SQL Server Management Studio или в пользовательских отчетах для доступа к наборам строк схемы с помощью синтаксиса SQL. Дополнительные сведения см. в разделе [Использование динамических административных представлений для мониторинга служб Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).<br /><br /> Написание кода ADOMD.NET, вызывающего набор строк схемы.<br /><br /> Выполнение метода XML для аналитики `Discover` непосредственно в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для получения сведений из набора строк схемы. Дополнительные сведения см. в статье [Метод Discover (XML для аналитики)](../../xmla/xml-elements-methods-discover.md).|  
|XML для аналитики|XML для аналитики — это API-интерфейс самого низкого уровня из доступных программисту служб Analysis Services; он является общим компонентом в основе всех методик доступа к данным в службах Analysis Services. XML для аналитики (XMLA) — это стандартный отраслевой XML-протокол, основанный на SOAP, поддерживающий универсальный доступ к данным в любом стандартном источнике многомерных данных через соединение по протоколу HTTP. В нем для формулирования запросов к многомерным данным и ответов на запросы используется SOAP. Если приложение будет работать не на платформе Windows, с помощью XML для аналитики можно осуществлять доступ к многомерной базе данных, выполняющейся на сервере Windows в сети. Дополнительные сведения см. в разделе [Разработка с использованием XMLA в службах Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).|  
|Язык ASSL|ASSL — это описательный термин, который относится к расширениям протокола XML для аналитики в службах Analysis Services. Расширения ASSL позволяют службам Analysis Services использовать XML для аналитики за пределами базовых задач протокола, в том числе для определения данных, изменения данных и поддержки управления данными.  В то время как методы Execute и Discover описываются протоколом XML для аналитики, ASSL добавляет следующие возможности:<br /><br /> Скрипты XML для аналитики<br /><br /> Определения объектов XML для аналитики<br /><br /> Команды XMLA<br /><br /> <br /><br /> Дополнительные сведения см. в разделе [Разработка на языке ASSL (язык ASSL)](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).|  
  
## <a name="see-also"></a>См. также  
 [Подключение к службам Analysis Services](../../instances/connect-to-analysis-services.md)   
 [Язык сценариев разработки с использованием Analysis Services &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Разработка с использованием XMLA в службах Analysis Services](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Доступ к данным табличной модели](../../tabular-models/tabular-model-data-access.md)  
  
  
