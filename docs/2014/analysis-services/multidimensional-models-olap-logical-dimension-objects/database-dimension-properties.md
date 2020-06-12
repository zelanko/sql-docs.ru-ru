---
title: Свойства измерения базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545196"
---
# <a name="database-dimension-properties"></a>Свойства измерений базы данных
  В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] характеристики измерения определяются метаданными для измерения, основанными на параметрах различных свойств измерения, а также в атрибутах или иерархиях, содержащихся в измерении. Следующая таблица содержит описания свойств измерений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
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
|`ProcessingGroup`|Указывает группу обработки. Значения: ByAttribute и ByTable. Значение по умолчанию — `ByAttribute`.|  
|`ProcessingMode`|Показывает, следует ли службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] производить индексирование и статистическую обработку во время работы или после нее.|  
|`ProcessingPriority`|Определяет приоритет обработки для измерения во время работы в фоновом режиме, например отложенная статистическая обработка, индексирование или кластеризация.|  
|`Source`|Определяет представление источника данных, к которому привязано измерение.|  
|`StorageMode`|Определяет режим хранения измерения.|  
|`Type`|Указывает тип измерения.|  
|`UnknownMember`|Показывает, видим ли неизвестный элемент.|  
|`UnknownMemberName`|Указывает заголовок (на языке по умолчанию для измерения) для неизвестного элемента измерения.|  
|`WriteEnabled`|Показывает, доступна ли обратная запись в измерение (зависит от прав доступа).|  
  
> [!NOTE]  
>  Дополнительные сведения о задании значений свойств ErrorConfiguration и UnknownMember при работе со значениями NULL и другими проблемами целостности данных см. в разделе [обработка проблем целостности данных в Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты и иерархии атрибутов](attributes-and-attribute-hierarchies.md)   
 [Пользовательские иерархии](user-hierarchies.md)   
 [Связи измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Измерения (службы Analysis Services — многомерные данные)](dimensions-analysis-services-multidimensional-data.md)  
  
  
