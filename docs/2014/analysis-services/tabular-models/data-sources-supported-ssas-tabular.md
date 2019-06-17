---
title: Поддерживаемые источники данных (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 345e733e5c1e90f637efab02a9942e307c2fb9f4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66067379"
---
# <a name="data-sources-supported-ssas-tabular"></a>Data Sources Supported (SSAS Tabular)
  В этом разделе описаны типы источников данных, которые могут использоваться в табличной модели.  
  
 Эта статья состоит из следующих разделов:  
  
-   [Поддерживаемые источники данных](#bkmk_supported_ds)  
  
-   [Неподдерживаемые источники](#bkmk_unsupported_ds)  
  
-   [Советы по выбору источников данных](#bkmk_tips)  
  
##  <a name="bkmk_supported_ds"></a> Поддерживаемые источники данных  
 Данные можно импортировать из источников данных, перечисленных в следующей таблице. При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных. Некоторые поставщики могут быть уже установлены в компьютер с другими приложениями, а в других случаях потребуется загрузить и установить необходимый поставщик.  
  
|||||  
|-|-|-|-|  
|`Source`|Версии|Тип файла|Поставщики <sup>1</sup>|  
|Базы данных Access|Microsoft Access 2003, 2007, 2010.|ACCDB или MDB|Поставщик OLE DB для ACE 14|  
|Реляционные базы данных SQL Server|Microsoft SQL Server 2005, 2008, 2008 R2; SQL Server 2012, Microsoft SQL Azure Database <sup>2</sup>|(неприменимо)|Поставщик OLE DB для SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server<br /><br /> Поставщик OLE DB для клиента SQL Server Native Client 10.0<br /><br /> Поставщик данных .NET Framework для клиента SQL|  
|SQL Server Parallel Data Warehouse (PDW) <sup>3</sup>|2008 R2|(неприменимо)|Поставщик OLE DB для SQL Server PDW|  
|Реляционные базы данных Oracle|Oracle 9i, 10g, 11g.|(неприменимо)|Поставщик OLE DB для Oracle<br /><br /> Поставщик данных .NET Framework для клиента Oracle<br /><br /> Поставщик данных .NET Framework для SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Реляционные базы данных Teradata|Teradata V2R6, V12|(неприменимо)|Поставщик TDOLEDB OLE DB<br /><br /> Поставщик данных .NET для Teradata|  
|Реляционные базы данных Informix||(неприменимо)|Поставщик OLE DB для Informix|  
|Реляционные базы данных IBM DB2|8.1|(неприменимо)|DB2OLEDB|  
|Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)|15.0.2|(неприменимо)|Поставщик OLE DB для Sybase|  
|Другие реляционные базы данных|(неприменимо)|(неприменимо)|Поставщик OLE DB или драйвер ODBC|  
|Текстовые файлы|(неприменимо)|TXT, TAB, CSV|Поставщик OLE DB ACE 14 для Microsoft Access|  
|Файлы Microsoft Excel|Excel 97-2003, 2007, 2010|XLSX, XLSM, XLSB, XLTX, XLTM|Поставщик OLE DB для ACE 14|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книга|Службы Microsoft SQL Server 2008 R2 Analysis Services|XLSX, XLSM, XLSB, XLTX, XLTM|ASOLEDB 10.5<br /><br /> (используется только с книгами [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , опубликованными на фермах SharePoint с установленным [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] )|  
|Куб служб Analysis Services|Службы Microsoft SQL Server 2005, 2008, 2008 R2 Analysis Services|(неприменимо)|ASOLEDB 10|  
|Веб-каналы данных<br /><br /> (используются для импорта данных из отчетов служб Reporting Services, сервисных документов Atom, Microsoft Azure Marketplace DataMarket и одиночных веб-каналов данных)|Формат Atom 1.0<br /><br /> Любая база данных или документ, который предоставляется как служба данных Windows Communication Foundation (WCF) (ранее служба данных ADO.NET).|ATOMSVC для сервисного документа, определяющего один или несколько потоков<br /><br /> ATOM для документа веб-канала Atom|Поставщик веб-каналов данных Microsoft для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Поставщик данных веб-каналов .NET Framework для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Файлы подключения к базе данных Office||ODC||  
  
 <sup>1</sup> также можно использовать поставщик OLE DB для ODBC.  
  
 <sup>2</sup> Дополнительные сведения о SQL Azure, см. в разделе веб-сайт [SQL Azure](https://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> Дополнительные сведения о SQL Server PDW см. в разделе веб-сайт [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> в некоторых случаях использование поставщика MSDAORA OLE DB может привести к ошибкам соединения, особенно в новых версиях Oracle. Если возникают ошибки, рекомендуется использовать один из других поставщиков для Oracle.  
  
##  <a name="bkmk_unsupported_ds"></a> Неподдерживаемые источники  
 В данной версии не поддерживается следующий тип источников данных.  
  
-   Нельзя импортировать серверные документы, например базы данных Access, уже опубликованные в SharePoint.  
  
##  <a name="bkmk_tips"></a> Советы по выбору источников данных  
  
1.  Импорт таблиц из реляционных баз данных сокращает число операций, поскольку при импорте для создания связей между таблицами в конструкторе моделей по *внешнему ключу* .  
  
2.  Импорт нескольких таблиц с последующим удалением ненужных таблиц также позволяет сократить число операций. Если таблицы импортируются поодиночке, то между ними может потребоваться создать связи вручную.  
  
3.  Столбцы из разных источников данных, содержащие схожие данные, служат основой для создания связей в конструкторе моделей. При использовании разнородных источников данных выберите таблицы со столбцами, которые можно сопоставить с таблицами в других источниках данных, содержащими идентичные или аналогичные данные.  
  
4.  Поставщики OLE DB иногда обеспечивают повышенную производительность для данных большого объема. Если нужно выбрать один из нескольких поставщиков, подходящих для некоторого источника данных, вначале следует проверить работу поставщика OLE DB.  
  
## <a name="see-also"></a>См. также  
 [Источники данных (табличные службы SSAS)](../data-sources-ssas-tabular.md)   
 [Импорт данных (табличные службы SSAS)](../import-data-ssas-tabular.md)  
  
  
