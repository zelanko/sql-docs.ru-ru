---
title: Создание подключения к данным (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.date: 11/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 73bf9e24ffb42ef93547097c53b5838a22292fda
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74190911"
---
# <a name="create-data-connection-strings---report-builder--ssrs"></a>Создание подключения к данным (построитель отчетов и службы SSRS)

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Чтобы включить данные в отчет [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] или [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы, следует предварительно создать *строку подключения* к нужному *источнику данных*. В этой статье описано, как создать строки подключения к источникам данных, а также представлены важные сведения об учетных данных для источников данных. Источник данных включает в себя тип источника данных, информацию о подключении и используемый тип учетных данных. Подробнее см. статью [Данные отчета в SQL Server Reporting Services (SSRS)](report-data-ssrs.md).
  
##  <a name="built-in-data-extensions"></a><a name="bkmk_DataConnections"></a> Встроенные модули обработки данных  
 По умолчанию в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включаются следующие расширения обработки данных: Microsoft SQL Server, База данных SQL Microsoft Azure и Microsoft SQL Server Analysis Services. Полный список источников данных и версий, поддерживаемых [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], см. в разделе [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
##  <a name="common-connection-string-examples"></a><a name="bkmk_connection_examples"></a> Примеры общих строк подключения  
 Строки подключения являются текстовым представлением свойств соединения для поставщика данных. Следующая таблица содержит примеры строк соединения для различных типов подключения к данным.  
 
 > [!NOTE]  
>  [ConnectionStrings.com](https://www.connectionstrings.com/) — это еще один ресурс, где можно получить примеры для строк подключения. 
  
|**Источник данных**|**Пример**|**Описание**|  
|---------------------|-----------------|---------------------|  
|База данных SQL Server на локальном сервере|`data source="(local)";initial catalog=AdventureWorks`|Задайте тип источника данных **Microsoft SQL Server**. Дополнительные сведения см. в разделе [Тип соединения SQL Server (службы SSRS)](../../reporting-services/report-data/sql-server-connection-type-ssrs.md).|  
|Экземпляр SQL Server<br /><br /> База данных|`Data Source=localhost\MSSQL13.<InstanceName>; Initial Catalog=AdventureWorks`|Задайте тип источника данных **Microsoft SQL Server**.|  
|База данных SQL Azure|`Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True`|Задайте тип источника данных **База данных SQL Microsoft Azure**. Дополнительные сведения см. в разделе [Тип соединения SQL Azure (службы SSRS)](../../reporting-services/report-data/sql-azure-connection-type-ssrs.md).|  
|Параллельное хранилище данных SQL Server|`HOST=<IP address>;database= AdventureWorks; port=<port>`|Задайте тип источника данных **Microsoft SQL Server Parallel Data Warehouse**. Дополнительные сведения см. в разделе [Тип соединения с параллельным хранилищем данных SQL Server (службы SSRS)](../../reporting-services/report-data/sql-server-parallel-data-warehouse-connection-type-ssrs.md).|  
|База данных служб Analysis Services на локальном сервере|`data source=localhost;initial catalog=Adventure Works DW`|Задайте тип источника данных **Microsoft SQL Server Analysis Services**. Дополнительные сведения см. в разделе [Тип соединения служб Analysis Services для многомерных выражений (службы SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md) или [Тип соединения служб Analysis Services для расширений интеллектуального анализа данных (службы SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md).|  
|Табличный шаблон базы данных служб Analysis Services с торговым представителем|`Data source=<servername>;initial catalog= Adventure Works DW;cube='Sales'`|Задайте тип источника данных **Microsoft SQL Server Analysis Services**. Укажите имя перспективы в параметре cube=. Дополнительные сведения см. в разделе [Перспективы (табличные службы SSAS)](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular).|  
|Сервер Oracle|`data source=myserver`|Задайте тип источника данных **Oracle**. Клиентские средства Oracle должны быть установлены на том компьютере, где работает конструктор отчетов, и на сервере отчетов. Дополнительные сведения см. в разделе [Тип соединения Oracle (службы SSRS)](../../reporting-services/report-data/oracle-connection-type-ssrs.md).|  
|Источник данных SAP NetWeaver BI|`DataSource=https://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla`|Задайте тип источника данных **SAP NetWeaver BI**. Дополнительные сведения см. в разделе [Тип соединения SAP NetWeaver BI (службы SSRS)](../../reporting-services/report-data/sap-netweaver-bi-connection-type-ssrs.md).|  
|Источник данных Hyperion Essbase|`Data Source=https://localhost:13080/aps/XMLA; Initial Catalog=Sample`|Задайте тип источника данных **Hyperion Essbase**. Дополнительные сведения см. в разделе [Тип соединения Hyperion Essbase (службы SSRS)](../../reporting-services/report-data/hyperion-essbase-connection-type-ssrs.md).|  
|Источник данных типа Teradata|`data source=`\<NNN>.\<NNN>.\<NNN>.\<NNN>`;`|Задайте тип источника данных **Teradata**. Строка подключения представляет собой IP-адрес в виде четырех полей, каждое из которых содержит от одного до трех числовых разрядов. Дополнительные сведения см. в разделе [Тип соединения Teradata (службы SSRS)](../../reporting-services/report-data/teradata-connection-type-ssrs.md).|  
|Источник данных типа Teradata|`Database=` *\<имя базы данных>* `; data source=` *\<NN*N *>.\<NNN>.\<NNN>.\<N*NN *>* `;Use X Views=False;Restrict to Default Database=True`|Установите для источника данных тип **Teradata**аналогично предыдущему примеру. Используйте только базу данных по умолчанию, указанную в теге Database, и не выполняйте автоматическое обнаружение связей данных.|  
|Источник XML-данных, веб-служба|`data source=https://adventure-works.com/results.aspx`|Задайте тип источника данных **XML**. Строка подключения является URL-адресом веб-службы, поддерживающей язык определения веб-служб (язык WSDL). Дополнительные сведения см. в разделе [Тип соединения XML (службы SSRS)](../../reporting-services/report-data/xml-connection-type-ssrs.md).|  
|Источник XML-данных, XML-документ|`https://localhost/XML/Customers.xml`|Задайте тип источника данных **XML**. Строкой соединения является URL-адрес XML-документа. 
|Источник XML-данных, внедренный XML-документ|*Пустой*|Задайте тип источника данных **XML**. XML-данные внедрены в определение отчета.|  
|SharePoint|`data source=https://MySharePointWeb/MySharePointSite/`|Задайте в качестве типа источника данных **Список SharePoint**.|  
| Набор данных Power BI Premium (начиная с Reporting Services версии 2019) | Сервер=powerbi://api.powerbi.com/v1.0/myorg/<workspacename>;начальный каталог=<YourDatasetName> | Задайте тип источника данных **Microsoft SQL Server Analysis Services**. |

  
 Если не удается подключиться к серверу отчетов с помощью **localhost**, убедитесь, что сетевой протокол для TCP/IP включен. Дополнительные сведения см. в статье [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).  
  
 Дополнительные сведения о конфигурациях, необходимых для подключения к этим типам источников данных, см. в разделах о подключении к данным конкретного типа статей [Добавление данных из внешних источников данных (службы SSRS)](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md) или [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
##  <a name="special-characters-in-a-password"></a><a name="bkmk_special_password_characters"></a> Специальные символы пароля  
 Если источник данных ODBC или SQL настроен так, что запрашивает пароль, или пароль включен в строку подключения, а пользователь вводит пароль со специальными символами, такими как знаки препинания, некоторые базовые драйверы источников данных не могут проверить специальные символы. При обработке отчета сообщение «Неверный пароль» может быть признаком этой ошибки. Если смена пароля нецелесообразна, администратор базы данных может сохранить соответствующие учетные данные на сервере как часть имени системного источника данных ODBC (DSN). Дополнительные сведения см. в разделе [OdbcConnection.ConnectionString](https://docs.microsoft.com/dotnet/api/system.data.odbc.odbcconnection.connectionstring) в документации по [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
##  <a name="expression-based-connection-strings"></a><a name="bkmk_Expressions_in_connection_strings"></a> Строки подключения на основе выражений  
 Строки подключения на основе выражений вычисляются во время выполнения. Например, можно задать источник данных в качестве параметра, включить ссылку на этот параметр в строку соединения и позволить пользователю выбрать источник данных для отчета. Например, у многонациональной компании есть серверы данных в нескольких странах. Благодаря тому, что строка соединения зависит от выражения, пользователь, выполняющий отчет о продажах, перед запуском может выбрать источник данных для определенной страны.  
  
 Следующий пример иллюстрирует использование выражения источника данных в строке соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Пример предполагает создание параметра отчета с именем `ServerName`:  
  
```  
="data source=" & Parameters!ServerName.Value & ";initial catalog=AdventureWorks"  
```  
  
 Выражения источника данных обрабатываются во время выполнения или во время предварительного просмотра отчета. Само выражение должно быть написано на языке [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. При определении выражения источника данных пользуйтесь следующими рекомендациями.  
  
-   Разрабатывайте отчет, используя статическую строку соединения. Для указания статической строки соединения выражение не используется (например, при выполнении этапов создания общего источника данных или источника данных, зависящего от отчета, определяется именно статическая строка соединения). Использование статической строки соединения позволяет устанавливать соединение с источником данных в конструкторе отчетов, чтобы получить результаты запроса, необходимые для создания отчетов.  
  
-   При определении соединения с источником данных не следует использовать общий источник данных. Нельзя использовать выражение источника данных для общего источника данных. Необходимо определить для отчета внедренный источник данных.  
  
-   Указывайте учетные данные отдельно от строки соединения. Можно использовать сохраненные учетные данные, запрашиваемые учетные данные или интегрированную защиту.  
  
-   Добавьте параметр отчета для указания источника данных. Для выбора значения параметра можно либо добавить статический список доступных значений (в таком случае доступными значениями должны быть источники данных, которые допустимо использовать с отчетом), либо определить запрос, извлекающий список источников данных во время выполнения.  
  
-   Удостоверьтесь, что все источники данных в списке используют одну и ту же схему базы данных. Конструирование отчета начинается с информации схемы. Если возникнет несоответствие между схемой, предназначенной для определения отчета, и схемой, фактически используемой отчетом во время выполнения, то выполнить отчет будет невозможно.  
  
-   Перед публикацией отчета замените статическую строку соединения выражением. Перед тем как заменять статическую строку соединения выражением, завершите конструирование отчета. Если в запросе используется выражение, этот отчет невозможно выполнить в конструкторе отчетов. Более того, список полей в области данных отчета и список параметров не будут обновляться автоматически.  

## <a name="next-steps"></a>Дальнейшие действия

[Данные отчета в SQL Server Reporting Services (SSRS)](report-data-ssrs.md)
[Создание и изменение совместно используемых источников данных](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md) .  
[Создание и изменение внедренных источников данных](../../reporting-services/report-data/create-and-modify-embedded-data-sources.md)   
[Определение свойств развертывания](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
[Задание учетных данных и сведениях о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
