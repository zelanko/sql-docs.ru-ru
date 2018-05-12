---
title: Поддерживаемые источники данных (службы SSAS — многомерные) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 907e6cc6deaa9617a4af93ab2080bfe495dacd0b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="supported-data-sources-ssas---multidimensional"></a>Поддерживаемые источники данных (службы SSAS — многомерные)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В этом разделе описываются типы источников данных, которые можно использовать в многомерной модели.  
  
##  <a name="bkmk_supported_ds"></a> Поддерживаемые источники данных  
 Данные можно получать из источников данных, перечисленных в следующей таблице. При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных. Некоторые поставщики могут быть уже установлены в компьютер с другими приложениями, а в других случаях потребуется загрузить и установить необходимый поставщик.  
  
> [!NOTE]  
>  Для подключения к сторонним базам данных можно использовать сторонние поставщики (например, Oracle OLE DB). Их поддержка осуществляется сторонними производителями.  
  
|||||  
|-|-|-|-|  
|Source|Версии|Тип файла|Поставщики*|  
|Базы данных Access|Microsoft Access 2010, 2013, 2016|ACCDB или MDB|Поставщик Microsoft OLE DB для Jet 4.0|  
|Реляционные базы данных SQL Server*|Microsoft SQL Server 2008, 2008 R2, 2012, 2014, 2016, [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)], хранилище данных Azure SQL, Microsoft Analytics Platform System (APS)<br /><br /> <br /><br /> Примечание. Дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)] см. на сайте [Azure.com](http://go.microsoft.com/fwlink/?LinkID=157856).<br /><br /> Примечание: Analytics Platform System (APS) ранее была известна как SQL Server Parallel данных хранилища (PDW). Изначально для подключения к PDW из служб Analysis Services требовался специальный поставщик данных. В SQL Server 2012 он был заменен. Начиная с SQL Server 2012, для подключения к PDW и APS используется SQL Server Native Client. Дополнительные сведения об APS см. на веб-сайте [Microsoft Analytics Platform System](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx).|(неприменимо)|Поставщик OLE DB для SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server<br /><br /> Поставщик OLE DB для собственного клиента SQL Server 11,0<br /><br /> Поставщик данных .NET Framework для клиента SQL|  
|Реляционные базы данных Oracle|Oracle 9i, 10g, 11g, 12g|(неприменимо)|Поставщик OLE DB для Oracle<br /><br /> Поставщик данных .NET Framework для клиента Oracle<br /><br /> Поставщик данных .NET Framework для SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Реляционные базы данных Teradata|Teradata V2R6, V12|(неприменимо)|Поставщик TDOLEDB OLE DB<br /><br /> Поставщик данных .NET для Teradata|  
|Реляционные базы данных Informix|V11.10|(неприменимо)|Поставщик OLE DB для Informix|  
|Реляционные базы данных IBM DB2|8.1|(неприменимо)|DB2OLEDB|  
|Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)|15.0.2|(неприменимо)|Поставщик OLE DB для Sybase|  
|Другие реляционные базы данных|(неприменимо)|(неприменимо)|Поставщик OLE DB|  
  
 \* Источники данных ODBC не поддерживаются в многомерных решениях. Хотя соединение будут обеспечивать сами службы Analysis Services, конструкторы в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , применяемые для создания решений, не могут подключаться к источнику данных ODBC, даже если используется драйвер MSDASQL. Если бизнес-требования включают источник данных ODBC, рассмотрите альтернативную возможность — создание табличного решения.  
  
 ** Для работы некоторых функций требуется запущенная локально реляционная база данных SQL Server. Это требуется для функции обратной записи и хранилища ROLAP — используемый источник данных должен быть реляционной базой данных SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые источники данных](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [Источники данных в многомерных моделях](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
