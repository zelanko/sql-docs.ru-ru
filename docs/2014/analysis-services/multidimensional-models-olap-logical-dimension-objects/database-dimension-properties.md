---
title: Свойства измерений базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e9b86509f0b4a5ab87102c43838cfa1b18376a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194334"
---
# <a name="database-dimension-properties"></a>Свойства измерений базы данных
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], характеристики измерения задаются метаданные для измерения, основываясь на настройках различных свойств измерения, а также на нем атрибутах или иерархиях, содержащихся в измерении. Следующая таблица содержит описания свойств измерений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`AttributeAllMemberName`|Задает имя элемента «Все» для атрибутов измерения.|  
|`Collation`|Задает параметры сортировки, применяемые в измерении.|  
|`CurrentStorageMode`|Содержит текущий режим хранения для измерения.|  
|`DependsOnDimension`|Содержит идентификатор другого измерения, от которого зависит данное (если такое имеется).|  
|`Description`|Содержит описание измерения.|  
|`ErrorConfiguration`|Настраиваемые параметры обработки ошибок для обработки ситуаций с повторяющимися ключами, неизвестными ключами, предельными значениями ошибок, действиями при обнаружении ошибки, файлом журнала ошибок и ключами со значением NULL.|  
|`ID`|Содержит уникальный идентификатор измерения.|  
|`Language`|Задает язык по умолчанию для измерения.|  
|`MdxMissingMemberMode`|Определяет, как обрабатываются пропущенные элементы для инструкций многомерных выражений.|  
|`MiningModelID`|Содержит идентификатор модели интеллектуального анализа данных, с которой связано измерение интеллектуального анализа данных. Применяется, только если измерение является измерением модели интеллектуального анализа данных.|  
|`Name`|Указывает имя измерения.|  
|`ProactiveCaching`|Определяет настройки упреждающего кэширования для измерения.|  
|`ProcessingGroup`|Указывает группу обработки. Значения: ByAttribute и ByTable. Значение по умолчанию — `ByAttribute`.|  
|`ProcessingMode`|Показывает, следует ли службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] производить индексирование и статистическую обработку во время работы или после нее.|  
|`ProcessingPriority`|Определяет приоритет обработки для измерения во время работы в фоновом режиме, например отложенная статистическая обработка, индексирование или кластеризация.|  
|`Source`|Определяет представление источника данных, к которому привязано измерение.|  
|`StorageMode`|Определяет режим хранения измерения.|  
|`Type`|Указывает тип измерения.|  
|`UnknownMember`|Показывает, видим ли неизвестный элемент.|  
|`UnknownMemberName`|Указывает заголовок (на языке по умолчанию для измерения) для неизвестного элемента измерения.|  
|`WriteEnabled`|Показывает, доступна ли обратная запись в измерение (зависит от прав доступа).|  
  
> [!NOTE]  
>  Дополнительные сведения о настройке значений свойства ErrorConfiguration и UnknownMember при работе со значениями null и других проблемах целостности данных, см. в разделе [обработка проблем целостности данных в службах аналитики 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](attributes-and-attribute-hierarchies.md)   
 [Пользовательские иерархии](user-hierarchies.md)   
 [Связи измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Измерения &#40;службы Analysis Services — многомерные данные&#41;](dimensions-analysis-services-multidimensional-data.md)  
  
  
