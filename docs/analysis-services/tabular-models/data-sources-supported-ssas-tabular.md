---
title: Поддерживаемые источники данных в SQL Server Analysis Services для табличных моделей 1200 | Документация Майкрософт
ms.date: 07/02/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a1ef7ae48e3d1500d08c9adba5e39db6214125c5
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597361"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1200-models"></a>Источники данных, поддерживаемые в SQL Server Analysis Services табличных моделей 1200
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  
В этой статье описаны типы источников данных, которые могут использоваться с табличных моделей служб SQL Server Analysis Services на 1200 и низкий уровень совместимости. 

Для моделей на уровне совместимости 1400, см. в разделе [поддерживаемые источники данных в SQL Server Analysis Services для табличных моделей 1400](data-sources-supported-ssas-tabular-1400.md).

Службы Azure Analysis Services, см. в разделе [источники данных, поддерживаемые в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).
  
##  <a name="bkmk_supported_ds"></a> Поддерживаемые источники данных для табличных моделей в памяти  
При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных. Некоторые поставщики могут устанавливаться с другими приложениями на компьютере. В других случаях может потребоваться скачать и установить поставщик.  
  
|||||  
|-|-|-|-|  
|`Source`|Версии|Тип файла|Поставщики|  
|Базы данных Access|Microsoft Access 2010 и более поздних версий|ACCDB или MDB|Поставщик ACE 14 OLE DB <sup> [1](#dnu)</sup>|  
|Реляционные базы данных SQL Server|SQL Server 2008 и более поздней версии, данные хранилища SQL Server 2008 и более поздних версий, Azure базы данных SQL, хранилище данных SQL Azure, Analytics Platform System (APS)<br /><br /> <br /><br /> Analytics Platform System (APS) ранее была известна как SQL Server Parallel данных хранилища (PDW). Изначально для подключения к PDW из служб Analysis Services требовался специальный поставщик данных. В SQL Server 2012 он был заменен. Начиная с SQL Server 2012, для подключения к PDW и APS используется SQL Server Native Client. |(неприменимо)|Поставщик OLE DB для SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server<br /><br /> Поставщик OLE DB для клиента SQL Server Native Client 10.0<br /><br /> Поставщик данных .NET Framework для клиента SQL|  
|Реляционные базы данных Oracle|Oracle 9i и более поздних версий|(неприменимо)|Поставщик OLE DB для Oracle<br /><br /> Поставщик данных .NET Framework для клиента Oracle<br /><br /> Поставщик данных .NET Framework для SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Реляционные базы данных Teradata|Teradata V2R6 и более поздних версий|(неприменимо)|Поставщик TDOLEDB OLE DB<br /><br /> Поставщик данных .NET для Teradata|  
|Реляционные базы данных Informix||(неприменимо)|Поставщик OLE DB для Informix|  
|Реляционные базы данных IBM DB2|8.1|(неприменимо)|DB2OLEDB|  
|Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)|15.0.2|(неприменимо)|Поставщик OLE DB для Sybase|  
|Другие реляционные базы данных|(неприменимо)|(неприменимо)|Поставщик OLE DB или драйвер ODBC|  
|Текстовые файлы|(неприменимо)|TXT, TAB, CSV|Поставщик ACE 14 OLE DB <sup> [1](#dnu)</sup> |  
|Файлы Microsoft Excel|Excel 2010 и более поздних версий|XLSX, XLSM, XLSB, XLTX, XLTM|Поставщик ACE 14 OLE DB <sup> [1](#dnu)</sup>|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книга|Microsoft SQL Server 2008 и более поздних версий, службы Analysis Services|XLSX, XLSM, XLSB, XLTX, XLTM|ASOLEDB 10.5<br /><br /> (используется только с книгами [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , опубликованными на фермах SharePoint с установленным [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] )|  
|Куб служб Analysis Services|Microsoft SQL Server 2008 и более поздних версий, службы Analysis Services|(неприменимо)|ASOLEDB 10|  
|Веб-каналы данных<br /><br /> (используются для импорта данных из отчетов служб Reporting Services, сервисных документов Atom, Microsoft Azure Marketplace DataMarket и одиночных веб-каналов данных)|Формат Atom 1.0<br /><br /> Любая база данных или документ, который предоставляется как служба данных Windows Communication Foundation (WCF) (ранее служба данных ADO.NET).|`.atomsvc` для сервисного документа, определяющего один или несколько потоков<br /><br /> ATOM для документа веб-канала Atom|Поставщик веб-каналов данных Microsoft для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Поставщик данных веб-каналов .NET Framework для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Файлы подключения к базе данных Office||ODC||  
 
<a name="dnu">[1] </a> Using **ACE 14 поставщик OLE DB** для подключения к типам данных файла **не рекомендуется**. Если необходимо сохранить моделей табличной совместимости 1200 и нижнего уровня, экспортировать данные в формат csv, импорт в базу данных SQL, подключиться к и импортировать из базы данных. Тем не менее, рекомендуется обновить уровень табличной совместимости 1400 (SQL Server 2017 и более поздние версии) и используйте **получить данные** в SSDT, чтобы выбрать и импортировать источник данных файла. Получите использует структурированных данных соединения с источниками данных, предоставляемые подсистема обработки данных Power Query, которые более стабильны, чем подключения поставщика ACE 14 OLE DB.  


##  <a name="bkmk_supported_ds_dq"></a> Поддерживаемые источники данных для моделей DirectQuery  
 DirectQuery — это альтернатива режиму хранения в памяти. В этом режиме вместо хранения всех данных внутри модели (и в ОЗУ после загрузки модели) запросы направляются непосредственно к серверным системам данных с последующим возвращением результатов. Так как службы Analysis Services должен составлять запросы в синтаксисе запроса собственной базы данных, определенное подмножество источников данных поддерживается для этого режима.  
  
Источник данных   |Версии  |Поставщики
---------|---------|---------
Microsoft SQL Server    |  2008 и более поздних версий      |       Поставщик OLE DB для SQL Server, поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server  
База данных Microsoft Azure SQL    |   All      |  Поставщик OLE DB для SQL Server, поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server            
Хранилище данных SQL Microsoft Azure     |   All     |  Поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server       
Системы платформы аналитики Microsoft SQL (APS)     |   All      |  Поставщик OLE DB для SQL Server, поставщик OLE DB для собственного клиента SQL Server, поставщик данных .NET Framework для клиента SQL Server       
|Microsoft SQL Server Always Encrypted <sup> [2](#ae)</sup> | 2016 и более поздних версий. 2014 и более ранних версий только в выпуске Enterprise. | Поставщик данных .NET Framework для клиента SQL
|База данных Azure SQL Always Encrypted <sup> [2](#ae)</sup>| All | Поставщик данных .NET Framework для клиента SQL
Реляционные базы данных Oracle     |  Oracle 9i и более поздних версий       |  Поставщик OLE DB для Oracle       
Реляционные базы данных Teradata    |  Teradata V2R6 и более поздних версий     | Поставщик данных .NET для Teradata    


### <a name="using-sql-server-analysis-services-with-always-encrypted"></a>С помощью SQL Server Analysis Services с помощью постоянного шифрования

<a name="ae">[2] </a> SQL Server Analysis Services могут выступать в качестве клиента для базы данных при помощи [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) в SQL Server или базы данных SQL Azure при следующих условиях: 

*  Главный ключ столбца, Защита зашифрованных столбцов должны быть сертификаты, хранящиеся в хранилище сертификатов Windows. Главные ключи столбцов, хранимых в хранилище ключей Azure не поддерживаются.   
*  Компьютер Windows, на котором установлены службы Analysis Services имеет сертификаты главного ключа столбца необходимо установить. Дополнительные сведения см. в разделе [Создание главных ключей столбцов, в Windows Store сертификата](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-windows-certificate-store).
*  Источник данных служб Analysis Services использует для подключения к SQL основан на .net Framework поставщика, а параметр шифрования столбца, необходимо включить свойство в источнике данных. .NET framework 4.6.1 или более поздней версии должна присутствовать на сервере служб Analysis Services.
*  Источник данных SQL Server или базы данных SQL должен быть *поставщика* тип источника данных, поддерживаемый уровень совместимости 1200. Он не будет работать с помощью Power Query *структурированных* источников данных, представленные в уровне совместимости 1400.
  
##  <a name="bkmk_tips"></a> Советы по выбору источников данных  
  
Импорт таблиц из реляционных баз данных сокращает число операций, поскольку при импорте для создания связей между таблицами в конструкторе моделей по *внешнему ключу* .  
  
Импорт нескольких таблиц с последующим удалением ненужных таблиц также позволяет сократить число операций. Если таблицы импортируются поодиночке, то между ними может потребоваться создать связи вручную.  
  
Столбцы из разных источников данных, содержащие схожие данные, служат основой для создания связей в конструкторе моделей. При использовании разнородных источников данных выберите таблицы со столбцами, которые можно сопоставить с таблицами в других источниках данных, содержащими идентичные или аналогичные данные.  
  
Поставщики OLE DB иногда обеспечивают повышенную производительность для больших объемов данных. Если нужно выбрать один из нескольких поставщиков, подходящих для некоторого источника данных, вначале следует проверить работу поставщика OLE DB.  

## <a name="see-also"></a>См. также

[Источники данных, поддерживаемые в SQL Server Analysis Services табличных моделей 1400](data-sources-supported-ssas-tabular-1400.md)

[Поддерживаемые источники данных в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
