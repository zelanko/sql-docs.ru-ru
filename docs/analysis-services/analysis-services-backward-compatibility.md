---
title: "Обратная совместимость служб SQL Server 2016 Analysis Services | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 618b6c3a-e20d-47a9-b2c6-6d848dfba05a
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f54505056125f11f3843a671a76136288f54b5d1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-backward-compatibility-sql-server-2016"></a>Обратная совместимость служб Analysis (SQL Server 2016)
[!INCLUDE[ssas-appliesto-sql2016](../includes/ssas-appliesto-sql2016.md)]

В этой статье описаны изменения в функциях и поведение между текущей и предыдущей версии.

## <a name="deprecated-features"></a>Устаревшие функции
Объект *нерекомендуемая функция* будет сокращаться из продукта в будущем выпуске, но по-прежнему поддерживается и включен в текущем выпуске для обеспечения обратной совместимости. Рекомендуется прекратить использование устаревшие функции в новых и существующих проектов для обеспечения совместимости с последующими выпусками.
  
Следующие функции являются устаревшими в этом выпуске.
  
|||  
|-|-|  
|**Режим, категория**|**Компонент**|  
|Multidimensional|Удаленные секции|  
|Multidimensional|Удаленные связанные группы мер|  
|Multidimensional|Многомерная обратная запись|  
|Multidimensional|Связанные измерения|   
|Multidimensional|Уведомления о таблицах SQL Server для упреждающего кэширования.  <br />В качестве замены можно использовать опрос для упреждающего кэширования. <br />См. разделы [Упреждающее кэширование (измерения)](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) и [Упреждающее кэширование (секции)](../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|Multidimensional|Кубы сеансов. Замена отсутствует.|  
|Multidimensional|Локальные кубы. Замена отсутствует.|  
|Табличный|Уровни совместимости 1100 и 1103 табличной модели не будут поддерживаться в будущем выпуске. Замена — можно задать на уровне совместимости 1200 или выше, преобразовав определения модели в табличных метаданных. См. раздел [Уровень совместимости табличных моделей в службах Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|Средства|Приложение SQL Server Profiler для перехвата трассировки<br /><br /> В качестве замены можно использовать профилировщик расширенных событий, встроенный в SQL Server Management Studio.  <br /> См. раздел [Мониторинг служб Analysis Services с помощью расширенных событий SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Средства|Воспроизведение трассировки с помощью приложения SQL Server Profiler <br />Замена. Замена отсутствует.|  
|Объекты управления трассировкой и интерфейсы API трассировки|Объекты Microsoft.AnalysisServices.Trace (содержат интерфейсы API для объектов трассировки и воспроизведения Analysis Services). Замена состоит из нескольких частей:<br /><br /> — настройка трассировки:  Microsoft.SqlServer.Management.XEvent;<br />— чтение трассировки: Microsoft.SqlServer.XEvent.Linq;<br />— воспроизведение трассировки: отсутствует.|  
  
> [!NOTE]  
>  Предыдущие объявления нерекомендуемых функций из [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] остаются в силе. Так как код поддержки этих функций еще не удален из продукта, многие из них все еще присутствуют в данной версии. При устаревшие ранее функции могут быть доступны, они все равно считаются устаревшим и могут быть физически удалены из продукта в любое время.  

## <a name="discontinued-features"></a>Неподдерживаемые функции
Объект *неподдерживаемой* был объявлен устаревшим в более ранних версиях. Он может по-прежнему включены в текущем выпуске, но больше не поддерживается. Неподдерживаемые функции могут быть удалены в будущем выпуске или обновить.

Следующие функции являются устаревшими в более раннем выпуске и больше не поддерживается в этом выпуске.

|||  
|-|-|  
|**Компонент**|**Замена или решение**|  
|[CalculationPassValue (многомерные выражения)](../mdx/calculationpassvalue-mdx.md)|Нет. Эта функция устарела в SQL Server 2005.|  
|[CalculationCurrentPass (многомерные выражения)](../mdx/calculationcurrentpass-mdx.md)|Нет. Эта функция устарела в SQL Server 2005.|  
|Подсказка оптимизатора запросов NON_EMPTY_BEHAVIOR|Нет. Эта функция устарела в SQL Server 2008.|  
|Сборки COM|Нет. Эта функция устарела в SQL Server 2008.|  
|Внутреннее свойство ячейки CELL_EVALUATION_LIST|Нет. Эта функция устарела в SQL Server 2005.|  
  
> [!NOTE]  
>  Предыдущие объявления нерекомендуемых функций из [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] остаются в силе. Так как код поддержки этих функций еще не удален из продукта, многие из них все еще присутствуют в данной версии. При устаревшие ранее функции могут быть доступны, они все равно считаются устаревшим и могут быть физически удалены из продукта в любое время.  

## <a name="breaking-changes"></a>Критические изменения
*Критическое изменение* приводит к прекращению работы модели данных, кода приложения или сценария после обновления модели или сервера.
  
### <a name="net-40-version-upgrade"></a>Обновление версии .NET 4.0  
 Клиентские библиотеки табличной модели объектов (TOM), ADOMD.NET и объекты управления Analysis Services (AMO) теперь модуля выполнения .NET 4.0. Это может быть критическим изменением для приложений, ориентированных на платформу .NET 3.5. Приложения, использующие более новые версии этих сборок, теперь должны ориентироваться на платформу .NET 4.0 или более поздней версии.  
  
### <a name="amo-version-upgrade"></a>Обновление версии объектов AMO  
 Этот выпуск является обновлением версии для [Management объекты служб Analysis Services &#40; Объекты AMO &#41; ](https://msdn.microsoft.com/library/mt436122.aspx) и является критическим изменением при определенных условиях.  Существующий код и сценарии, которые вызывают объекты AMO, продолжают работать как прежде, если обновление произведено из предыдущей версии. Тем не менее если вам нужно *перекомпилировать* приложения и использовать экземпляр SQL Server 2016 Analysis Services, необходимо добавить следующее пространство имен, чтобы код или сценарий работали:  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 Если в коде делается ссылка на сборку Microsoft.AnalysisServices, необходимо использовать пространство имен [Microsoft.AnalysisServices.Core](https://msdn.microsoft.com/library/microsoft.analysisservices.core.aspx) . Объекты, которые ранее содержались только в пространстве имен **Microsoft.AnalysisServices** и одинаково используются в табличных и многомерных сценариях, в этом выпуске перемещены в основное пространство имен.  Например, API, связанные с сервером, перемещены в основное пространство имен.  
  
 Несмотря на множество доступных пространств имен, оба вида существуют в одной сборке (Microsoft.AnalysisServices.dll).  
  
### <a name="xevent-discover-changes"></a>Изменения XEvent DISCOVER  
 Для лучшей поддержки XEvent ОБНАРУЖЕНИЕ потоковой передачи в среде SSMS для SQL Server 2016 Analysis Services `DISCOVER_XEVENT_TRACE_DEFINITION` заменяется следующие трассировках XEvent:  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  

## <a name="behavior-changes"></a>Изменения в поведении
*Изменения в работе* влияют на поведение функций или их взаимодействие в текущей версии по сравнению с предыдущими версиями SQL Server.
  
Примерами изменения в работе могут служить перемена значений по умолчанию, необходимость в ручной настройке для завершения обновления или восстановления функциональности и новая реализация существующей функции.
  
Здесь перечислены функции, которые изменены в этом выпуске, но в то же время не нарушают работу существующей модели или код после обновления.
  
### <a name="analysis-services-in-sharepoint-mode"></a>Службы Analysis Services в режиме интеграции с SharePoint
 Запуск мастера настройки Power Pivot в виде задачи после установки больше не требуется. Это верно для всех поддерживаемых версий SharePoint для загрузки моделей из текущего SQL Server 2016 Analysis Services.
  
### <a name="directquery-mode-for-tabular-models"></a>Режим DirectQuery в табличных моделях
 *DirectQuery* — это режим доступа к данным для табличных моделей, при котором выполнение запроса происходит на серверной реляционной базе данных с получением результирующего набора в режиме реального времени. Он часто используется для очень больших наборов данных, которые не помещаются в памяти, или быстро меняющихся данных, если необходимо вернуть самые последние данные с помощью запросов к табличной модели.
  
 DirectQuery выступает в качестве режима доступа к данным в последних нескольких выпусках. В SQL Server 2016 Analysis Services реализация немного изменена, при условии, что табличная модель находится на уровне совместимости 1200 или выше. Режим DirectQuery имеет меньше ограничений, чем раньше. Кроме того, изменены свойства базы данных.
  
 При использовании DirectQuery для существующей табличной модели ее можно сохранить на текущем уровне совместимости (1100 или 1103) и работать далее в том же режиме и на том же уровне. Кроме того можно обновить до 1200 или выше, чтобы использовать улучшения, внесенные в DirectQuery.
  
 Нет не обновление на месте модели DirectQuery, так как параметры предыдущих уровней совместимости не имеют точных аналогов в новых уровней совместимости 1200 и выше. При наличии существующей табличной модели, работающей в режиме DirectQuery, следует открыть модель в SQL Server Data Tools, отключить этот режим, задайте **уровень совместимости** свойство 1200 или выше, а затем изменить DirectQuery свойства. В разделе [режим DirectQuery](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md) подробные сведения.


## <a name="see-also"></a>См. также:
[Обратная совместимость служб Analysis (SQL Server 2017)](analysis-services-backward-compatibility-sql2017.md)
