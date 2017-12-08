---
title: "Обратная совместимость служб аналитики SQL Server 2017 г. | Документы Microsoft"
ms.date: 07/11/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: analysis-services
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
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 57a03d325a7415f08fd073ea805e022935f3fce7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Обратная совместимость служб Analysis (SQL 2017 г.)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

В этой статье описаны изменения в функциях и поведение между выпуском текущего и предыдущего выпуска.

## <a name="deprecated-features"></a>Устаревшие функции
Объект *нерекомендуемая функция* будет сокращаться из продукта в будущем выпуске, но по-прежнему поддерживается и включен в текущем выпуске для обеспечения обратной совместимости. Рекомендуется прекратить использование устаревшие функции в новых и существующих проектов для обеспечения совместимости с последующими выпусками.

Следующие функции являются устаревшими в этом выпуске.
  
|||  
|-|-|  
|**Режим, категория**|**Компонент**|
|Multidimensional|Интеллектуальный анализ данных|
|Multidimensional|Удаленные связанные группы мер|
|Табличный|Моделей на уровне совместимости 1100 и 1103|
|Табличный|Свойства табличной модели объекта: Column.IsDefaultImage Column.TableDetailPosition Column.IsDefaultLabel,|


## <a name="discontinued-features"></a>Неподдерживаемые функции
Объект *неподдерживаемой* был объявлен устаревшим в более ранних версиях. Он может по-прежнему включены в текущем выпуске, но больше не поддерживается. Неподдерживаемые функции могут быть удалены в будущем выпуске или обновить.

Следующие функции являются устаревшими в более раннем выпуске и больше не поддерживается в этом выпуске.
  
|||  
|-|-|  
|**Режим, категория**|**Компонент**|  
|Табличный|Значение свойства VertipaqPagingPolicy памяти (2), включить разбиение на страницы на диск с использованием памяти сопоставленные файлы.|
|Multidimensional|Удаленные секции|  
|Multidimensional|Удаленные связанные группы мер|  
|Multidimensional|Многомерная обратная запись|  
|Multidimensional|Связанные измерения|
|Инструменты|Приложение SQL Server Profiler для перехвата трассировки<br /><br /> В качестве замены можно использовать профилировщик расширенных событий, встроенный в SQL Server Management Studio.  <br /> См. раздел [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Средства|Воспроизведение трассировки с помощью приложения SQL Server Profiler <br />Замена. Замена отсутствует.|  
|Объекты управления трассировкой и интерфейсы API трассировки|Объекты Microsoft.AnalysisServices.Trace (содержат интерфейсы API для объектов трассировки и воспроизведения Analysis Services). Замена состоит из нескольких частей:<br /><br /> -Настройка трассировки: Microsoft.SqlServer.Management.xevent;<br />-Чтение трассировки: Microsoft.SqlServer.xevent.Linq.<br />— воспроизведение трассировки: отсутствует.|  

## <a name="breaking-changes"></a>Критические изменения
Объект *критическое изменение* вызывает функцию, модели данных, код приложения или сценария к прекращению работы после обновления до текущего выпуска.

Отсутствуют критические изменения в этом выпуске.

## <a name="behavior-changes"></a>Изменения в поведении
Объект *изменение поведения* влияет на работу одной функции в текущей версии по сравнению с предыдущим выпуском. Описываются только существенных изменений в поведении. Изменения в пользовательский интерфейс, не включаются.

Изменения в MDSCHEMA_MEASUREGROUP_DIMENSIONS и DISCOVER_CALC_DEPENDENCY, описанные в [новые возможности CTP-версия SQL Server 2017 г 2.1 для служб Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/05/18/whats-new-in-sql-server-2017-ctp-2-1-for-analysis-services/) объявления.


## <a name="see-also"></a>См. также:
[Обратная совместимость служб Analysis (SQL Server 2016)](analysis-services-backward-compatibility.md)
