---
title: Анализ потока данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e67c5448a6625b37c7fb17bc24ea6bdd7cb879ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061599"
---
# <a name="analysis-of-data-flow"></a>Анализ потока данных
  Можно использовать [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` представление для анализа потока данных пакетов базы данных. Это представление отображает строку каждый раз, когда компонент потока данных передает данные в компонент, находящийся ниже в иерархии. Подобная информация дает полное представление о строках, отправляемых для каждого компонента.  
  
> [!NOTE]  
>  Чтобы получать необходимые сведения с помощью представления catalog.execution_data_statistics, уровнем ведения журнала должен быть **Подробно** .  
  
 В следующем примере отображается число строк, отправленных компонентами пакета.  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 В следующем примере подсчитывается количество строк, отправляемых в миллисекунду каждым компонентом при конкретном запуске пакета. Вычисляются следующие значения:  
  
-   **total_rows** — сумма всех строк, отправленных компонентом  
  
-   **wall_clock_time_ms** — общее время выполнения каждого компонента, в миллисекундах  
  
-   **num_rows_per_millisecond** — количество строк, отправляемых каждым компонентом в миллисекунду  
  
 `HAVING` Предложение используется для предотвращения возникновения в вычислениях ошибки деления на ноль.  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Отладка потока данных](troubleshooting/debugging-data-flow.md)  
  
 [Устранение неполадок инструментов с помощью отчетов](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a>См. также  
 [Данные потоков данных](data-flow/data-in-data-flows.md)  
  
  
