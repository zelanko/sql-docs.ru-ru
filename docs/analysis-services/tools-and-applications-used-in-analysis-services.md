---
title: "Средств и приложений, используемых в службах Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 2d286657c8264cc0b1fa82b87a2978cd60387506
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="tools-and-applications-used-in-analysis-services"></a>Средства и приложения, использующиеся в службах Analysis Services
  Найдите средства и приложения, которые понадобятся для создания моделей Analysis Services и управление развертывания базы данных.  
  
## <a name="analysis-services-model-designers"></a>Конструкторы моделей Analysis Services  
 Модели создаются с помощью шаблонов проектов в SQL Server Data Tools (SSDT), оболочка Visual Studio. Шаблоны проектов предоставляют конструкторы моделей для создания объектов модели данных, составляющих решение Analysis Services. Средство SSDT доступно для бесплатной загрузки обновляется ежемесячно.

 **[Скачать SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)** 
  
 У моделей имеется параметр уровня совместимости, который определяет доступность функций и версию служб Analysis Services, которые запускают модель.  Ли вы определяете находится на данном уровне совместимости определяется в рамках конструктором моделей.  
  
 Табличные модели, используя новые функциональные возможности, такие как BIM-файлы в табличном формате JSON и двунаправленная перекрестная фильтрация, должны быть созданы и обновлены на уровне совместимости 1200 или выше.  
  
 Если требуется более низкий уровень совместимости, возможно, так как вы хотите развернуть модель в более ранней версии служб Analysis Services, можно по-прежнему используется конструктор моделей в SSDT. Более новые версии средства поддерживают создание моделей любого типа (табличные или многомерные) на любом уровне совместимости.   

## <a name="administrative-tools"></a>Средства администрирования  
  
 SQL Server Management Studio (SSMS) — основное средство администрирования для всех компонентов SQL Server, включая службы Analysis Services. Среда SSMS является бесплатной загрузки, обновляются ежемесячно. 
  
**[Загрузите SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)** 
  
 Среда SSMS включает расширенные события (xEvents), предоставляя Упрощенная альтернатива трассировки приложения SQL Server Profiler для мониторинга активности и диагностики проблем на серверах служб Azure Analysis Services и SQL Server 2016. Дополнительные сведения см. в статье [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) .  
  
### <a name="sql-server-profiler"></a>Приложение SQL Server Profiler  
 Несмотря на то, что официально приложение SQL Server Profiler признано устаревшим в пользу xEvents, это простой способ мониторинга подключений, выполнения запросов MDX и выполнения других операций на сервере. Профилировщик SQL Server устанавливается по умолчанию. Его можно найти с помощью приложения SQL Server на приложения в Windows.  
  
### <a name="powershell"></a>PowerShell  
 Для выполнения многих административных задач можно использовать команды PowerShell. В разделе [Справочник PowerShell](../analysis-services/powershell/analysis-services-powershell-reference.md) для получения дополнительной информации.  
  
### <a name="community-and-third-party-tools"></a>Средства сообщества и сторонние средства  
 Примеры кодов сообщества см. на [странице CodePlex Analysis Services](http://sqlsrvanalysissrvcs.codeplex.com/) . Рекомендации по сторонним средствам, которые поддерживают Analysis Services, см. на[Форумах](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) .  
  
## <a name="see-also"></a>См. также:  
 [Уровень совместимости многомерной базы данных](../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Уровень совместимости для табличных моделей](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
