---
title: Средства и приложения, использующиеся в службах Analysis Services | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8d3ecb5de4c70c09bc367b9008f5d62c6a23faef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162281"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>Средства и приложения, использующиеся в службах Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  Найдите средства и приложения, необходимые вам для создания моделей Analysis Services и управление развернутых баз данных.  
  
## <a name="analysis-services-model-designers"></a>Конструкторы моделей Analysis Services  
 Модели создаются с помощью шаблонов проектов в SQL Server Data Tools (SSDT), оболочке Visual Studio. Шаблоны проектов предоставляют конструкторы моделей для создания объектов модели данных, составляющих решение Analysis Services. SSDT является бесплатной загрузки из Интернета обновляется ежемесячно.

 **[Скачать SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)** 
  
 У моделей имеется параметр уровня совместимости, который определяет доступность функций и версию служб Analysis Services, которые запускают модель.  Ли вы можно указать, что находится на данном уровне совместимости определяется в рамках конструктором моделей.  
  
 Табличные модели, используя новые функциональные возможности, такие как bim-файлы в табличном формате JSON и двунаправленный кросс-фильтрации, должны быть созданы и обновлены на уровне совместимости 1200 или выше.  
  
 Если требуется более низкий уровень совместимости, возможно потому, что вы хотите развернуть модель в более ранней версии служб Analysis Services, можно по-прежнему использовать конструктор моделей в SSDT. Более новые версии средства поддерживают создание моделей любого типа (табличные или многомерные) на любом уровне совместимости.   

## <a name="administrative-tools"></a>Средства администрирования  
  
 SQL Server Management Studio (SSMS) — это основное средство администрирования для всех компонентов SQL Server, включая службы Analysis Services. Среда SSMS — бесплатной загрузки из Интернета обновляется ежемесячно. 
  
**[Скачивание SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)** 
  
 SSMS включает расширенные события (xEvents), предоставляя облегченной альтернативой трассировок SQL Server Profiler, используемых для мониторинга активности и диагностики проблем в SQL Server 2016 и серверов Azure Analysis Services. Дополнительные сведения см. в статье [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) .  
  
### <a name="sql-server-profiler"></a>Приложение SQL Server Profiler  
 Несмотря на то, что официально приложение SQL Server Profiler признано устаревшим в пользу xEvents, это простой способ мониторинга подключений, выполнения запросов MDX и выполнения других операций на сервере. Профилировщик SQL Server устанавливается по умолчанию. Его можно найти с помощью приложения SQL Server в приложениях в Windows.  
  
### <a name="powershell"></a>PowerShell  
 Для выполнения многих административных задач можно использовать команды PowerShell. См. в разделе [Справочник по PowerShell](../analysis-services/powershell/analysis-services-powershell-reference.md) Дополнительные сведения.  
  
### <a name="community-and-third-party-tools"></a>Средства сообщества и сторонние средства  
 Примеры кодов сообщества см. на [странице CodePlex Analysis Services](http://sqlsrvanalysissrvcs.codeplex.com/) . Рекомендации по сторонним средствам, которые поддерживают Analysis Services, см. на[Форумах](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) .  
  
## <a name="see-also"></a>См. также  
 [Уровень совместимости многомерной базы данных](../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Уровень совместимости табличных моделей](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
