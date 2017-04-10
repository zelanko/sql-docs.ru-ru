---
title: "Нерекомендуемые функции служб Analysis Services в SQL Server 2016 | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Обратная совместимость служб Analysis Services"
  - "Обратная совместимость служб SSAS"
  - "SQL Server Analysis Services, backward compatibility"
  - "устаревшие возможности [службы Analysis Services]"
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 52
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 52
---
# Нерекомендуемые функции служб Analysis Services в SQL Server 2016
  *Нерекомендуемая функция* — это функция, которая будет удалена из продукта в будущем выпуске, но по-прежнему поддерживается и присутствует в текущем выпуске для обеспечения обратной совместимости. Обычно нерекомендуемая функция удаляется в основном выпуске, часто в пределах двух выпусков после первоначального объявления. К примеру, нерекомендуемые функции, объявленные в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , скорее всего, не будут поддерживаться в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 **Функции, не поддерживаемые в следующем основном выпуске SQL Server**  
  
|||  
|-|-|  
|**Категория**|**Компонент**|  
|Multidimensional|Удаленные секции|  
|Multidimensional|Удаленные связанные группы мер|  
|Multidimensional|Многомерная обратная запись|  
|Multidimensional|Связанные измерения|  
  
 **Функции, не поддерживаемые в будущем основном выпуске SQL Server**  
  
|||  
|-|-|  
|**Категория**|**Компонент**|  
|Multidimensional|Уведомления о таблицах SQL Server для упреждающего кэширования.  <br />В качестве замены можно использовать опрос для упреждающего кэширования. <br />См. разделы [Упреждающее кэширование (измерения)](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) и [Упреждающее кэширование (секции)](../Topic/Proactive%20Caching%20\(Partitions\).md).|  
|Multidimensional|Кубы сеансов. Замена отсутствует.|  
|Multidimensional|Локальные кубы. Замена отсутствует.|  
|Табличный|Уровни совместимости 1100 и 1103 табличной модели не будут поддерживаться в будущем выпуске. В качестве замены можно задать уровень совместимости 1200, преобразовав определения модели в табличные метаданные. См. раздел [Compatibility Level for Tabular models in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|Средства|Приложение SQL Server Profiler для перехвата трассировки<br /><br /> В качестве замены можно использовать профилировщик расширенных событий, встроенный в SQL Server Management Studio.  <br /> См. раздел [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Средства|Воспроизведение трассировки с помощью приложения SQL Server Profiler <br />Замена. Замена отсутствует.|  
|Объекты управления трассировкой и интерфейсы API трассировки|Объекты Microsoft.AnalysisServices.Trace (содержат интерфейсы API для объектов трассировки и воспроизведения Analysis Services). Замена состоит из нескольких частей:<br /><br /> — настройка трассировки:  Microsoft.SqlServer.Management.XEvent;<br />— чтение трассировки: Microsoft.SqlServer.XEvent.Linq;<br />— воспроизведение трассировки: отсутствует.|  
  
> [!NOTE]  
>  Предыдущие объявления нерекомендуемых функций из [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] остаются в силе. Так как код поддержки этих функций еще не удален из продукта, многие из них все еще присутствуют в данной версии. Хотя объявленные ранее нерекомендуемыми функции могут быть доступны, они все равно считаются таковыми и могут быть физически удалены из продукта в любой момент в ходе выпуска [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Настоятельно рекомендуется избегать использования нерекомендуемых функций во всех новых моделях и приложениях на основе [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## См. также  
 [Analysis Services Backward Compatibility](../analysis-services/analysis-services-backward-compatibility.md)   
 [Неподдерживаемые функции служб Analysis Services в SQL Server 2016](../analysis-services/discontinued-analysis-services-functionality-in-sql-server-2016.md)  
  
  