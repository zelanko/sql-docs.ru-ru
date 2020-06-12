---
title: Поддерживаемые источники данных (многомерные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Analysis Services, data sources
- data sources [Analysis Services], about data sources
- Analysis Services, data sources
- connections [Analysis Services]
- SSAS, data sources
ms.assetid: c97e0f8d-7ddd-4941-8b51-e7832f30fbbe
author: minewiskan
ms.author: owend
ms.openlocfilehash: e750e286d7a58bee8c6979515fe163119175d529
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547340"
---
# <a name="data-sources-supported-ssas-multidimensional"></a>Поддерживаемые источники данных (многомерные службы SSAS)
  В этом разделе описываются типы источников данных, которые можно использовать в многомерной модели.  
  
##  <a name="supported-data-sources"></a><a name="bkmk_supported_ds"></a>Поддерживаемые источники данных  
 Данные можно получать из источников данных, перечисленных в следующей таблице. При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных. Некоторые поставщики могут быть уже установлены в компьютер с другими приложениями, а в других случаях потребуется загрузить и установить необходимый поставщик.  
  
> [!NOTE]  
>  Для подключения к сторонним базам данных можно использовать сторонние поставщики (например, Oracle OLE DB). Их поддержка осуществляется сторонними производителями.  
  
|||||  
|-|-|-|-|  
|Источник|Версии|Тип файла|Поставщики <sup>1</sup>|  
|Базы данных Access|Microsoft Access 2007, 2010, 2013.|ACCDB или MDB|Поставщик Microsoft OLE DB для Jet 4.0|  
|SQL Server реляционные базы данных <sup>5</sup>|Microsoft SQL Server 2005, 2008, 2008 R2, 2012, 2014 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] <sup>2</sup>, SQL Server Parallel Data Warehouse (PDW) <sup>3</sup>|(неприменимо)|Поставщик OLE DB для SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server 11,0<br /><br /> Поставщик данных .NET Framework для клиента SQL|  
|Реляционные базы данных Oracle|Oracle 9i, 10g, 11g.|(неприменимо)|Поставщик OLE DB для Oracle<br /><br /> Поставщик данных .NET Framework для клиента Oracle<br /><br /> Поставщик данных .NET Framework для SQL Server<br /><br /> MSDAORA OLE DB поставщик <sup>4</sup><br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Реляционные базы данных Teradata|Teradata V2R6, V12|(неприменимо)|Поставщик TDOLEDB OLE DB<br /><br /> Поставщик данных .NET для Teradata|  
|Реляционные базы данных Informix|V11.10|(неприменимо)|Поставщик OLE DB для Informix|  
|Реляционные базы данных IBM DB2|8.1|(неприменимо)|DB2OLEDB|  
|Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)|15.0.2|(неприменимо)|Поставщик OLE DB для Sybase|  
|Другие реляционные базы данных|(неприменимо)|(неприменимо)|Поставщик OLE DB|  
  
 <sup>1</sup> источники данных ODBC не поддерживаются для многомерных решений. Хотя соединение будут обеспечивать сами службы Analysis Services, конструкторы в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , применяемые для создания решений, не могут подключаться к источнику данных ODBC, даже если используется драйвер MSDASQL. Если бизнес-требования включают источник данных ODBC, рассмотрите альтернативную возможность — создание табличного решения.  
  
 <sup>2</sup> дополнительные сведения см [!INCLUDE[ssSDS](../../includes/sssds-md.md)] . в разделе на [Azure.Microsoft.com](https://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)] PDW см. в статье [SQL Server Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> в некоторых случаях использование поставщика MSDAORA OLE DB может привести к ошибкам подключения, особенно с более новыми версиями Oracle. Если возникают ошибки, рекомендуется использовать один из других поставщиков для Oracle.  
  
 <sup>5</sup> для некоторых функций требуется SQL Server реляционной базы данных, которая работает в локальной среде. Это требуется для функции обратной записи и хранилища ROLAP — используемый источник данных должен быть реляционной базой данных SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Поддерживаемые источники данных &#40;табличные&#41;SSAS](../tabular-models/data-sources-supported-ssas-tabular.md)   
 [Источники данных в многомерных моделях](data-sources-in-multidimensional-models.md)   
 [Представления источников данных в многомерных моделях](data-source-views-in-multidimensional-models.md)  
  
  
