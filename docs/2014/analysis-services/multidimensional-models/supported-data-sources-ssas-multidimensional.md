---
title: Поддерживаемые источники данных (многомерные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
manager: craigg
ms.openlocfilehash: c80d2736082e99d2e08f4c30fe311d98beff137a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169644"
---
# <a name="data-sources-supported-ssas-multidimensional"></a>Источники данных, поддерживаемых (многомерные службы SSAS)
  В этом разделе описываются типы источников данных, которые можно использовать в многомерной модели.  
  
##  <a name="bkmk_supported_ds"></a> Поддерживаемые источники данных  
 Данные можно получать из источников данных, перечисленных в следующей таблице. При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных. Некоторые поставщики могут быть уже установлены в компьютер с другими приложениями, а в других случаях потребуется загрузить и установить необходимый поставщик.  
  
> [!NOTE]  
>  Для подключения к сторонним базам данных можно использовать сторонние поставщики (например, Oracle OLE DB). Их поддержка осуществляется сторонними производителями.  
  
|||||  
|-|-|-|-|  
|Source|Версии|Тип файла|Поставщики <sup>1</sup>|  
|Базы данных Access|Microsoft Access 2007, 2010, 2013.|ACCDB или MDB|Поставщик Microsoft OLE DB для Jet 4.0|  
|Реляционные базы данных SQL Server <sup>5</sup>|Microsoft SQL Server 2005, 2008, 2008 R2, 2012, 2014 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] <sup>2</sup>, SQL Server Parallel Data Warehouse (PDW) <sup>3</sup>|(неприменимо)|Поставщик OLE DB для SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server 11,0<br /><br /> Поставщик данных .NET Framework для клиента SQL|  
|Реляционные базы данных Oracle|Oracle 9i, 10g, 11g.|(неприменимо)|Поставщик OLE DB для Oracle<br /><br /> Поставщик данных .NET Framework для клиента Oracle<br /><br /> Поставщик данных .NET Framework для SQL Server<br /><br /> Поставщик MSDAORA OLE DB <sup>4</sup><br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Реляционные базы данных Teradata|Teradata V2R6, V12|(неприменимо)|Поставщик TDOLEDB OLE DB<br /><br /> Поставщик данных .NET для Teradata|  
|Реляционные базы данных Informix|V11.10|(неприменимо)|Поставщик OLE DB для Informix|  
|Реляционные базы данных IBM DB2|8.1|(неприменимо)|DB2OLEDB|  
|Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)|15.0.2|(неприменимо)|Поставщик OLE DB для Sybase|  
|Другие реляционные базы данных|(неприменимо)|(неприменимо)|Поставщик OLE DB|  
  
 <sup>1</sup> источники данных ODBC не поддерживаются в многомерных решениях. Хотя соединение будут обеспечивать сами службы Analysis Services, конструкторы в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , применяемые для создания решений, не могут подключаться к источнику данных ODBC, даже если используется драйвер MSDASQL. Если бизнес-требования включают источник данных ODBC, рассмотрите альтернативную возможность — создание табличного решения.  
  
 <sup>2</sup> Дополнительные сведения см. в разделе [!INCLUDE[ssSDS](../../includes/sssds-md.md)]на [azure.microsoft.com](http://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> Дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)] PDW, см. в разделе [SQL Server Parallel Data Warehouse](http://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> в некоторых случаях использование поставщика MSDAORA OLE DB может привести к ошибкам соединения, особенно в новых версиях Oracle. Если возникают ошибки, рекомендуется использовать один из других поставщиков для Oracle.  
  
 <sup>5</sup> некоторых функций требуется SQL Server реляционной базы данных, которая работает локально. Это требуется для функции обратной записи и хранилища ROLAP — используемый источник данных должен быть реляционной базой данных SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Источники данных, поддерживаемые &#40;табличные службы SSAS&#41;](../tabular-models/data-sources-supported-ssas-tabular.md)   
 [Источники данных в многомерных моделях](data-sources-in-multidimensional-models.md)   
 [Представления источников данных в многомерных моделях](data-source-views-in-multidimensional-models.md)  
  
  
