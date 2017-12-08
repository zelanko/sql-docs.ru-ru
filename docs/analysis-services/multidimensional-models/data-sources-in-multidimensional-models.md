---
title: "Источники данных в многомерных моделях | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [Analysis Services]
- Analysis Services objects, data sources
- storing data [Analysis Services], data sources
- data sources [Analysis Services], about data sources
- security [Analysis Services], data sources
- data sources [Analysis Services]
- storage [Analysis Services], data sources
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
caps.latest.revision: "45"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7be6a20c985f7af2f6560856f0e2b361e22949ba
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="data-sources-in-multidimensional-models"></a>Источники данных в многомерных моделях
  Все данные, которые вы импортируете или загружаете в многомерную модель, происходят из внешнего источника данных. Обычно исходные данные поступают из хранилища данных, разработанного для составления отчетов, однако они могут поступать из любой реляционной базы данных, которая обращается прямо или косвенно через посредника, например пакет [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Объект **источника данных** в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] задает прямое соединение с внешним источником данных. Помимо физического расположения, объект источника данных указывает строку соединения, поставщика данных, учетные данные и другие свойства, управляющие поведением соединения.  
  
 Сведения, предоставляемые объектом источника данных, используются при выполнении следующих операций.  
  
-   Возврат сведений о схеме и других метаданных, используемых для генерирования представлений источников данных в модели.  
  
-   Запрос или загрузка данных в модель во время обработки.  
  
-   Выполнение запросов к многомерным моделям или моделям интеллектуального анализа данных, использующим режим хранения ROLAP.  
  
-   Считывание или запись удаленных секций.  
  
-   Подключение к связанным объектам и синхронизация цели с источником.  
  
-   Выполнение операций обратной записи для обновления данных таблицы фактов, которая хранится в реляционной базе данных.  
  
 Если новая многомерная модель строится снизу вверх, следует начать с создания объекта источника данных, а затем использовать его для создания следующего объекта — **представления источников данных**. Представление источника данных — это уровень абстракции данных в модели. Обычно оно создается после создания объекта источника данных на основе схемы исходной базы данных. Однако можно выбрать и другие способы создания модели, например, начать с кубов, измерений и создания наилучшей схемы для вашего проекта.  
  
 Каждой модели, независимо от способа создания, требуется хотя бы один объект источника данных, который задает соединение с источником данных. Можно создать несколько объектов источника данных в одной модели для использования данных из разных источников или изменять свойства соединения для конкретных объектов.  
  
 Управлять объектами источника данных можно независимо от других объектов в модели. Свойства созданного источника данных можно позже изменить, а затем выполнить предварительную обработку модели для правильной выборки данных.  
  
## <a name="related-topics-and-tasks"></a>Связанные темы и задачи  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Поддерживаемые источники данных (службы SSAS — многомерные базы данных)](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)|Описание типов источников данных, которые можно использовать в многомерной модели.|  
|[Создание источника данных (многомерные службы SSAS)](../../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)|Описывает добавление объекта источника данных в многомерную модель.|  
|[Удаление источника данных в обозревателе решений (многомерные службы SSAS)](../../analysis-services/multidimensional-models/delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|Эта процедура позволяет удалить объект источника данных из многомерной модели.|  
|[Задание свойств источника данных (многомерные службы SSAS)](../../analysis-services/multidimensional-models/set-data-source-properties-ssas-multidimensional.md)|Описывает каждое свойство и объясняет, как его задать.|  
|[Задание параметров олицетворения (службы SSAS — многомерные)](../../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)|Объясняет настройку параметров в диалоговом окне «Сведения об олицетворении».|  
  
## <a name="see-also"></a>См. также  
 [Объекты баз данных (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [Логическая архитектура (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Источники данных и привязки &#40; Многомерные службы SSAS &#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
