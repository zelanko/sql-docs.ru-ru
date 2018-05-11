---
title: Доступ к данным многомерной модели (службы Analysis Services — многомерные данные) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a79e5e085508683429817f6dad4f284a4b42b80e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="multidimensional-model-data-access-analysis-services---multidimensional-data"></a>Доступ к данным многомерной модели (службы Analysis Services — многомерные данные)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 Для создания отчетов, использующих базы данных служб Analysis Services, которые содержат аналитические данные, можно использовать построитель отчетов или конструктор отчетов. И построитель отчетов, и конструктор отчетов содержат конструктор запросов многомерных выражений, который можно использовать для ввода или конструирования инструкций многомерных выражений, извлекающих данные из доступного источника данных. Дополнительные сведения см. в разделах [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md), [Тип соединения служб Analysis Services для многомерных выражений (службы SSRS)](../../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md).  
  
### <a name="performancepoint-dashboards"></a>Панели мониторинга PerformancePoint  
 Панели мониторинга PerformancePoint используются для создания в SharePoint оценочных листов, в которых показатели бизнеса сравниваются со стандартными величинами. PerformancePoint включает поддержку соединений с многими мерными данными служб Analysis Services. Дополнительные сведения см. в разделе [Создание подключений к данным служб Analysis Services (службы PerformancePoint)](http://go.microsoft.com/fwlink/?linkid=232471).  
  
### <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 Конструкторы моделей и отчетов используют средства SQL Server Data Tools для построения решений, которые включают многомерные модели. При развертывании решения в экземпляре служб Analysis Services создается база данных, к которой в дальнейшем производятся подключения из Excel, служб Reporting Services и других клиентских приложений бизнес-аналитики.  
  
 Средства SQL Server Data Tools основаны на оболочке Visual Studio, и для хранения и упорядочивания моделей в них используются проекты. Дополнительные сведения см. в разделе [Создание многомерных моделей с помощью SQL Server Data Tools (SSDT)](../../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md).  
  
### <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio  
 Для администраторов баз данных среда SQL Server Management Studio служит интегрированной средой управления экземплярами SQL Server, в том числе и экземплярами служб Analysis Services и многомерными базами данных. Дополнительные сведения см. в разделах [Среда SQL Server Management Studio](http://msdn.microsoft.com/library/66a6b7b1-de6a-4161-82bd-98ded486947b) и [Подключение к службам Analysis Services](../../../analysis-services/instances/connect-to-analysis-services.md).  
  
##  <a name="bkmk_querylang"></a> Языки запросов  
 Язык многомерных выражений (MDX) является отраслевым стандартом языка запросов и вычислений, используемым при извлечении данных из баз данных OLAP. В службах Analysis Services язык многомерных выражений (MDX) — это язык запросов, используемый для извлечения данных, но также поддерживающий определение данных и изменение данных. Редакторы многомерных выражений встроены в среду SQL Server Management Studio, в службы Reporting Services и в средства SQL Server Data Tools. Редакторы многомерных выражений можно использовать для создания нерегламентированных запросов или скриптов, допускающих многократное использование, если операцию над данными необходимо повторять.  
  
 Некоторые инструменты и приложения, например Microsoft Excel, используют конструкции многомерных выражений во внутренних механизмах для выполнения запросов к источникам данных служб Analysis Services. Многомерные выражения также можно использовать программным образом, включая их в запросы XMLA Execute.  
  
 Дополнительные сведения о многомерных выражениях см. по следующим ссылкам.  
  
 [Запрос многомерных данных с помощью многомерных выражений](../../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
 [Ключевые понятия многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
 [Основные принципы запросов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
 [Основные понятия о сценариях многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
##  <a name="bkmk_api"></a> Программные интерфейсы  
 При разработке пользовательского приложения, использующего многомерные данные, скорее всего, будет использоваться один из следующих способов доступа к данным.  
  
-   **XML для аналитики**. Используйте XML для аналитики, когда требуется обеспечить совместимость с широким рядом различных операционных систем и протоколов. XML для аналитики обеспечивает максимальную гибкость, но часто за счет снижения производительности и усложнения программирования.  
  
-   **Клиентские библиотеки**. Используйте клиентские библиотеки служб Analysis Services, такие как ADOMD.NET, AMO и OLE DB, при необходимости получить программный доступ к данным из клиентских приложений, работающих под управлением операционной системы Microsoft Windows. Клиентские библиотеки помещают XML для аналитики в объектную модель и реализуют оптимизации, которые повышают производительность.  
  
     Клиентские библиотеки ADOMD.NET и AMO предназначены для приложений, написанных на управляемом коде. Используйте OLE DB для служб Analysis Services, если приложение написано на машинном коде.  
  
 В следующих таблицах содержатся дополнительные сведения и ссылки по клиентским библиотекам, используемым для соединения со службами Analysis Services из пользовательских приложений.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|Управляющие объекты служб Analysis Services (AMO)|Объекты AMO — это основная объектная модель для администрирования экземпляров служб Analysis Services и многомерных баз данных из кода. Например, среда SQL Server Management Studio использует объекты AMO для поддержки администрирования серверов и баз данных. Дополнительные сведения см. в разделе [Разработка объектов управления аналитикой (объекты AMO)](../../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).|  
|ADOMD.NET|ADOMD.NET служит основной объектной моделью для создания многомерных данных и доступа к ним в пользовательских приложениях. Для получения сведений служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью стандартных интерфейсов доступа к данным платформы Microsoft .NET в управляемом пользовательском приложении можно использовать ADOMD.NET. Дополнительные сведения см. в разделах [Разработка с использованием ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md) и [Программирование клиента ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md).|  
|Поставщик OLE DB служб Analysis Services (MSOLAP.dll)|Для доступа к службам [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] из неуправляемого API-интерфейса программными средствами можно использовать собственный поставщик данных OLE DB. Дополнительные сведения см. в разделе [Поставщик OLE DB служб Analysis Services (службы Analysis Services — многомерные данные)](http://msdn.microsoft.com/library/cdeecd50-1d91-4162-a4a2-01c7799b02a8).|  
|Наборы строк схемы|Таблицы наборов строк схемы — это структуры данных, содержащие описательные сведения о развернутой на сервере многомерной модели, а также о выполняющихся на сервере в настоящий момент действиях. Программист может выполнять запросы к таблицам наборов строк схемы из клиентских приложений, чтобы просматривать хранящиеся на экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] метаданные, а также для получения с него вспомогательной информации и данных отслеживания. Наборы строк схемы можно использовать со следующими программными интерфейсами: OLE DB, OLE DB для служб Analysis Services, OLE DB для интеллектуального анализа данных и XML для аналитики. Дополнительные сведения см. в разделе [Наборы строк схемы служб Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md).<br /><br /> В следующем списке описывается несколько подходов к использованию наборов строк схемы:<br /><br /> — Выполнение запросов к динамическим административным представлениям из среды SQL Server Management Studio или в пользовательских отчетах для доступа к наборам строк схемы с помощью синтаксиса SQL. Дополнительные сведения см. в разделе [Использование динамических административных представлений для мониторинга служб Analysis Services](../../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).<br /><br /> — Написание кода ADOMD.NET, вызывающего набор строк схемы.<br /><br /> — Выполнение метода XMLA **Discover** непосредственно в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для получения сведений из набора строк схемы. Дополнительные сведения см. в статье [Метод Discover (XML для аналитики)](../../../analysis-services/xmla/xml-elements-methods-discover.md).|  
|XML для аналитики|XML для аналитики — это API-интерфейс самого низкого уровня из доступных программисту служб Analysis Services; он является общим компонентом в основе всех методик доступа к данным в службах Analysis Services. XML для аналитики (XMLA) — это стандартный отраслевой XML-протокол, основанный на SOAP, поддерживающий универсальный доступ к данным в любом стандартном источнике многомерных данных через соединение по протоколу HTTP. В нем для формулирования запросов к многомерным данным и ответов на запросы используется SOAP. Если приложение будет работать не на платформе Windows, с помощью XML для аналитики можно осуществлять доступ к многомерной базе данных, выполняющейся на сервере Windows в сети. Дополнительные сведения см. в разделе [Разработка с использованием XMLA в службах Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).|  
|Язык ASSL|ASSL — это описательный термин, который относится к расширениям протокола XML для аналитики в службах Analysis Services. В то время как методы Execute и Discover описываются протоколом XML для аналитики, ASSL добавляет следующие возможности:<br /><br /> — Скрипт XML для аналитики<br /><br /> — Определения объектов XML для аналитики<br /><br /> — Команды XML для аналитики<br /><br /> Расширения ASSL позволяют службам Analysis Services использовать XML для аналитики за пределами базовых задач протокола, в том числе для определения данных, изменения данных и поддержки управления данными. Дополнительные сведения см. в разделе [Разработка на языке ASSL (язык ASSL)](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).|  
  
## <a name="see-also"></a>См. также  
 [Подключение к службам Analysis Services](../../../analysis-services/instances/connect-to-analysis-services.md)   
 [Развертывание с помощью функций анализа служб языка сценариев &#40;ASSL&#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [Доступ к данным табличной модели](../../../analysis-services/tabular-models/tabular-model-data-access.md)  
  
  
