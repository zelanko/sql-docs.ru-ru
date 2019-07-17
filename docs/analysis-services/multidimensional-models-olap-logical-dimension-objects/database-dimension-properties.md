---
title: Свойства измерений базы данных | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7c7944ab279f2b036a3acd7cf75bd775d0ec6d6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68180776"
---
# <a name="database-dimension-properties"></a>Свойства измерений базы данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], характеристики измерения задаются метаданные для измерения, основываясь на настройках различных свойств измерения, а также на нем атрибутах или иерархиях, содержащихся в измерении. Следующая таблица содержит описания свойств измерений служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Свойство|Описание|  
|--------------|-----------------|  
|**AttributeAllMemberName**|Задает имя элемента «Все» для атрибутов измерения.|  
|**Параметры сортировки**|Задает параметры сортировки, применяемые в измерении.|  
|**CurrentStorageMode**|Содержит текущий режим хранения для измерения.|  
|**Раздел о DependsOnDimension**|Содержит идентификатор другого измерения, от которого зависит данное (если такое имеется).|  
|**Описание**|Содержит описание измерения.|  
|**ErrorConfiguration**|Настраиваемые параметры обработки ошибок для обработки ситуаций с повторяющимися ключами, неизвестными ключами, предельными значениями ошибок, действиями при обнаружении ошибки, файлом журнала ошибок и ключами со значением NULL.|  
|**Идентификатор**|Содержит уникальный идентификатор измерения.|  
|**Язык**|Задает язык по умолчанию для измерения.|  
|**MdxMissingMemberMode**|Определяет, как обрабатываются пропущенные элементы для инструкций многомерных выражений.|  
|**MiningModelID**|Содержит идентификатор модели интеллектуального анализа данных, с которой связано измерение интеллектуального анализа данных. Применяется, только если измерение является измерением модели интеллектуального анализа данных.|  
|**Name**|Указывает имя измерения.|  
|**ProactiveCaching**|Определяет настройки упреждающего кэширования для измерения.|  
|**ProcessingGroup**|Указывает группу обработки. Значения: ByAttribute и ByTable. Значение по умолчанию — **ByAttribute**.|  
|**ProcessingMode**|Показывает, следует ли службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] производить индексирование и статистическую обработку во время работы или после нее.|  
|**ProcessingPriority**|Определяет приоритет обработки для измерения во время работы в фоновом режиме, например отложенная статистическая обработка, индексирование или кластеризация.|  
|**Source**|Определяет представление источника данных, к которому привязано измерение.|  
|**StorageMode**|Определяет режим хранения измерения.|  
|**Тип**|Указывает тип измерения.|  
|**UnknownMember**|Показывает, видим ли неизвестный элемент.|  
|**UnknownMemberName**|Указывает заголовок (на языке по умолчанию для измерения) для неизвестного элемента измерения.|  
|**WriteEnabled**|Показывает, доступна ли обратная запись в измерение (зависит от прав доступа).|  
  
> [!NOTE]  
>  Дополнительные сведения о настройке значений свойства ErrorConfiguration и UnknownMember при работе со значениями null и других проблемах целостности данных, см. в разделе [обработка проблем целостности данных в службах аналитики 2005](http://go.microsoft.com/fwlink/?LinkId=81891).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Пользовательские иерархии](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Связи измерений](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Измерения (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
