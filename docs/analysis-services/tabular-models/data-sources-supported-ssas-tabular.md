---
title: "Data Sources Supported (SSAS Tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 28
---
# Data Sources Supported (SSAS Tabular)
  В этом разделе описаны типы источников данных, которые могут использоваться в табличной модели.  
  
##  <a name="bkmk_supported_ds"></a> Поддерживаемые источники данных для моделей в памяти  
 Данные можно импортировать из источников данных, перечисленных в следующей таблице. При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных. Некоторые поставщики могут быть уже установлены в компьютер с другими приложениями, а в других случаях потребуется загрузить и установить необходимый поставщик.  
  
|||||  
|-|-|-|-|  
|Source|Версии|Тип файла|Поставщики|  
|Базы данных Access|Microsoft Access 2010 и более поздних версий|ACCDB или MDB|Поставщик OLE DB для ACE 14|  
|Реляционные базы данных SQL Server|Microsoft SQL Server 2008 и более поздних версий, Microsoft SQL Server Data Warehouse 2008 и более поздних версий, база данных SQL Microsoft Azure, Microsoft Analytics Platform System (APS)<br /><br /> <br /><br /> Обратите внимание, что система APS ранее была известна как SQL Server Parallel Datawarehouse (PDW). Изначально для подключения к PDW из служб Analysis Services требовался специальный поставщик данных. В SQL Server 2012 он был заменен. Начиная с SQL Server 2012, для подключения к PDW и APS используется SQL Server Native Client. Дополнительные сведения об APS см. на веб-сайте [Microsoft Analytics Platform System](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx).|(неприменимо)|Поставщик OLE DB для SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server<br /><br /> Поставщик OLE DB для клиента SQL Server Native Client 10.0<br /><br /> Поставщик данных .NET Framework для клиента SQL|  
|Реляционные базы данных Oracle|Oracle 9i и более поздних версий|(неприменимо)|Поставщик OLE DB для Oracle<br /><br /> Поставщик данных .NET Framework для клиента Oracle<br /><br /> Поставщик данных .NET Framework для SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Реляционные базы данных Teradata|Teradata V2R6 и более поздних версий|(неприменимо)|Поставщик TDOLEDB OLE DB<br /><br /> Поставщик данных .NET для Teradata|  
|Реляционные базы данных Informix||(неприменимо)|Поставщик OLE DB для Informix|  
|Реляционные базы данных IBM DB2|8.1|(неприменимо)|DB2OLEDB|  
|Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)|15.0.2|(неприменимо)|Поставщик OLE DB для Sybase|  
|Другие реляционные базы данных|(неприменимо)|(неприменимо)|Поставщик OLE DB или драйвер ODBC|  
|Текстовые файлы|(неприменимо)|TXT, TAB, CSV|Поставщик OLE DB ACE 14 для Microsoft Access|  
|Файлы Microsoft Excel|Excel 2010 и более поздних версий|XLSX, XLSM, XLSB, XLTX, XLTM|Поставщик OLE DB для ACE 14|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книга|Microsoft SQL Server 2008 и более поздних версий, службы Analysis Services|XLSX, XLSM, XLSB, XLTX, XLTM|ASOLEDB 10.5<br /><br /> (используется только с книгами [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], опубликованными на фермах SharePoint с установленным [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)])|  
|Куб служб Analysis Services|Microsoft SQL Server 2008 и более поздних версий, службы Analysis Services|(неприменимо)|ASOLEDB 10|  
|Веб-каналы данных<br /><br /> (используются для импорта данных из отчетов служб Reporting Services, сервисных документов Atom, Microsoft Azure Marketplace DataMarket и одиночных веб-каналов данных)|Формат Atom 1.0<br /><br /> Любая база данных или документ, который предоставляется как служба данных Windows Communication Foundation (WCF) (ранее служба данных ADO.NET).|ATOMSVC для сервисного документа, определяющего один или несколько потоков<br /><br /> ATOM для документа веб-канала Atom|Поставщик веб-каналов данных Microsoft для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Поставщик данных веб-каналов .NET Framework для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Файлы подключения к базе данных Office||ODC||  
  
  
##  <a name="bkmk_supported_ds_dq"></a> Поддерживаемые источники данных для моделей DirectQuery  
 DirectQuery — это альтернатива режиму хранения в памяти. В этом режиме вместо хранения всех данных внутри модели (и в ОЗУ после загрузки модели) запросы направляются непосредственно к серверным системам данных с последующим возвращением результатов. Так как службы Analysis Services составляют запросы в синтаксисе собственного запроса к базе данных, этот режим поддерживает незначительное подмножество источников данных.  
  
Источник данных   |Версии  |Поставщики
---------|---------|---------
Microsoft SQL Server    |  2008 и более поздних версий      |       Поставщик OLE DB для SQL Server, поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server  
База данных Microsoft Azure SQL    |   все      |  Поставщик OLE DB для SQL Server, поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server            
Хранилище данных SQL Microsoft Azure     |   все     |  Поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server       
Системы платформы аналитики Microsoft SQL (APS)     |   все      |  Поставщик OLE DB для SQL Server, поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server       
Реляционные базы данных Oracle     |  Oracle 9i и более поздних версий       |  Поставщик OLE DB для Oracle       
Реляционные базы данных Teradata    |  Teradata V2R6 и более поздних версий     | Поставщик данных .NET для Teradata    

  
##  <a name="bkmk_tips"></a> Советы по выбору источников данных  
  
Импорт таблиц из реляционных баз данных сокращает число операций, поскольку при импорте для создания связей между таблицами в конструкторе моделей по *внешнему ключу* .  
  
Импорт нескольких таблиц с последующим удалением ненужных таблиц также позволяет сократить число операций. Если таблицы импортируются поодиночке, то между ними может потребоваться создать связи вручную.  
  
Столбцы из разных источников данных, содержащие схожие данные, служат основой для создания связей в конструкторе моделей. При использовании разнородных источников данных выберите таблицы со столбцами, которые можно сопоставить с таблицами в других источниках данных, содержащими идентичные или аналогичные данные.  
  
Поставщики OLE DB иногда обеспечивают повышенную производительность для данных большого объема. Если нужно выбрать один из нескольких поставщиков, подходящих для некоторого источника данных, вначале следует проверить работу поставщика OLE DB.  
  
## См. также  
 [Источники данных (табличные службы SSAS)](../../analysis-services/tabular-models/data-sources-ssas-tabular.md)   
 [Импорт данных (табличные службы SSAS)](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)  
  
  