---
title: "Элемент BaseProperty (CSDLBI) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 79d391ef3ac0388187c91dac96859172a347effc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="baseproperty-element-csdlbi"></a>Элемент BaseProperty (CSDLBI)
  Элемент BaseProperty — сложный тип, который служит основой для других элементов.  
  
 Эти атрибуты могут появляться в столбцах и в мерах.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент BaseProperty.  
  
|Название|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Выравнивание|Нет|Имя, присвоенное элементу (столбцу, мере, свойству навигации, иерархии или уровню), определяемое реализацией типа Member.|  
|FormatString|Нет|Отображаемое имя элемента.|  
|IsRightToLeft|Нет|Логическое значение, указывающее, содержит ли текстовое поле текст для чтения справа налево.<br /><br /> Если этот атрибут опускается, используется параметр по умолчанию (модели).|  
|SortDirection|Нет|Значение, указывающее, как обычно сортируются значения поля. Содержимое этого атрибута определяется простым типом SortDirection.<br /><br /> Если этот атрибут не указан, то направление сортировки определяется по типу данных поля.|  
|Единицы измерения|Нет|Символ, который применяется к значениям полей для задания единиц измерения.<br /><br /> Если не указано, то единицы неизвестны.|  
  
## <a name="alignment-element"></a>Элемент Alignment  
 Этот простой тип определяет формат имени, используемый для однозначного определения элементов.  
  
|Значение|Description|  
|-----------|-----------------|  
|None|Использовать имя атрибута.|  
|Контекст|Использовать имя входящей связи.|  
|Объединить|Объединить имя входящей связи и имя свойства согласно правилам текущей грамматики.|  
  
## <a name="sortdirection-element"></a>Элемент SortDirection  
 Этот простой тип определяет формат имени, используемый для однозначного определения элементов.  
  
|Значение|Description|  
|-----------|-----------------|  
|None|Использовать имя атрибута.|  
|Контекст|Использовать имя входящей связи.|  
|Объединить|Объединить имя входящей связи и имя свойства.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модели табличного объекта на совместимость уровни 1050 до 1103](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
