---
title: Свойства куба | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d2b99362f242ff7f815e9ceb9f67db9c80983c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727650"
---
# <a name="cube-properties"></a>Свойства куба
  Кубы имеют ряд свойств, изменение которых оказывает непосредственное влияние на их работу. Эти свойства перечислены в следующей таблице.  
  
> [!NOTE]  
>  Некоторые свойства устанавливаются автоматически при создании куба и не могут быть изменены.  
  
 Дополнительные сведения о настройке свойств куба см. в разделе [конструктор кубов &#40;Analysis Services многомерных данных&#41;](../cube-designer-analysis-services-multidimensional-data.md).  
  
|Свойство|Description|  
|--------------|-----------------|  
|`AggregationPrefix`|Общий префикс, используемый для имен агрегатов.|  
|`Collation`|Код локали (LCID) и флаг сравнения, отделенный символом подчеркивания, например Latin1_General_C1_AS.|  
|`DefaultMeasure`|Содержит многомерное выражение, определяющее меру для куба по умолчанию.|  
|`Description`|Содержит описание куба, которое может отображаться в клиентских приложениях.|  
|`ErrorConfiguration`|Содержит настраиваемые параметры обработки ошибок, которые относятся к обработке ситуаций с повторяющимися и неизвестными ключами, действиями при обнаружении ошибок и их предельному числу, файлам журналов ошибок и обработки ключей NULL.|  
|`EstimatedRows`|Указывает предполагаемое количество строк в кубе.|  
|`ID`|Содержит уникальный идентификатор куба.|  
|`Language`|Указывает идентификатор языка куба по умолчанию.|  
|`Name`|Указывает понятное имя куба.|  
|`ProactiveCaching`|Определяет настройки упреждающего кэша для куба.|  
|`ProcessingMode`|Показывает, следует ли производить индексирование и статистическую обработку во время обработки или после нее. Параметры являются **обычными** или `lazy`.|  
|`ProcessingPriority`|Определяет приоритет обработки куба во время фоновых операций, например отложенных статистических вычислений или индексирования. Значение по умолчанию — **0**.|  
|`ScriptCacheProcessingMode`|Определяет, когда должен создаваться кэш скрипта: во время обработки или после нее. Параметры являются **обычными** и `lazy`.|  
|`ScriptErrorHandlingMode`|Определяет обработку ошибок. Может принимать значение `IgnoreNone` или `IgnoreAll`.|  
|`Source`|Отображает представление источника данных, используемое для куба.|  
|`StorageLocation`|Указывает для куба место хранения в файловой системе. Если не задано иное, то место хранения наследуется из базы данных, содержащей объект куба.|  
|`StorageMode`|Указывает для куба режим хранения. Значения: `MOLAP`, `ROLAP`или`HOLAP``.`|  
|`Visible`|Определяет, отображается куб или скрыт.|  
  
> [!NOTE]  
>  Дополнительные сведения о задании значений для свойства ErrorConfiguration при работе со значениями NULL и другими проблемами целостности данных см. [в разделе Обработка проблем целостности данных в Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>См. также:  
 [Упреждающее кэширование &#40;секций&#41;](partitions-proactive-caching.md)  
  
  
