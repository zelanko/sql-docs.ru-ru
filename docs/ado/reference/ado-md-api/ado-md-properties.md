---
description: Свойства многомерных объектов ADO
title: Свойства объекты данных ActiveX (MD) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, properties
- properties [ADO MD]
ms.assetid: 11ca7e42-ab6a-47da-ab32-55abab663069
author: rothja
ms.author: jroth
ms.openlocfilehash: 9f6628f0f172e81a490d0abd6a8cb2ae2a73679e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776674"
---
# <a name="ado-md-properties"></a>Свойства многомерных объектов ADO

|Свойство.|Описание:|  
|-|-|  
|[ActiveConnection](./activeconnection-property-ado-md.md)|Указывает объект **подключения** ADO, к которому в настоящий момент принадлежит текущий набор ячеек или каталог.|  
|[Caption](./caption-property-ado-md.md)|Указывает текст подписи, используемый при отображении объекта **уровня** или **элемента** .|  
|[ChildCount](./childcount-property-ado-md.md)|Указывает количество элементов, для которых текущий объект- **элемент** является родительским в иерархии.|  
|[Children](./children-property-ado-md.md)|Возвращает коллекцию **элементов** , для которых текущий **элемент** является родительским в иерархии.|  
|[Count](../ado-api/count-property-ado.md)|Указывает количество объектов в коллекции.|  
|[Depth](./depth-property-ado-md.md)|Указывает количество уровней между **уровнем** и корнем уровня иерархии.|  
|[Описание](./description-property-ado-md.md)|Возвращает текстовое описание текущего объекта.|  
|[DimensionCount](./dimensioncount-property-ado-md.md)|Указывает количество измерений на оси.|  
|[DrilledDown](./drilleddown-property-ado-md.md)|Указывает, следуют ли какие-либо потомки непосредственно за элементом на оси.|  
|[FilterAxis](./filteraxis-property-ado-md.md)|Указывает сведения о фильтре для текущего набора ячеек.|  
|[Item](./item-property-ado-md-cellset.md)|Извлекает ячейку из набора ячеек, используя ее координаты.|  
|[Item](../ado-api/item-property-ado.md)|Возвращает конкретный элемент коллекции по имени или порядковому номеру.|  
|[FormattedValue](./formattedvalue-property-ado-md.md)|Указывает отформатированное отображение значения ячейки.|  
|[LevelDepth](./leveldepth-property-ado-md.md)|Указывает количество уровней между корневым элементом иерархии и элементом.|  
|[LevelName](./levelname-property-ado-md.md)|Указывает имя уровня элемента.|  
|[Имя](./name-property-ado-md.md)|Указывает имя объекта.|  
|[Ordinal (ячейка)](./ordinal-property-ado-md-cell.md)|Однозначно определяет ячейку по ее положению в наборе ячеек.|  
|[Ordinal (расположение)](./ordinal-property-ado-md-position.md)|Уникально определяет расположение вдоль оси.|  
|[Parent](./parent-property-ado-md.md)|Указывает элемент, являющийся родительским по отношению к текущему элементу в иерархии.|  
|[парентсамеаспрев](./parentsameasprev-property-ado-md.md)|Указывает, совпадает ли родительский элемент данного элемента позиционирования с родительским элементом непосредственно предыдущего элемента.|  
|[Source](./source-property-ado-md.md)|Указывает источник данных в наборе ячеек.|  
|[Состояние](./state-property-ado-md.md)|Указывает текущее состояние набора ячеек.|  
|[Тип](./type-property-ado-md.md)|Указывает тип текущего элемента.|  
|[UniqueName](./uniquename-property-ado-md.md)|Указывает на однозначное имя для текущего объекта.|  
|[Значение](./value-property-ado-md.md)|Указывает значение текущей ячейки.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по объекты данных ActiveX (MD) API](./ado-md-object-model.md?view=sql-server-ver15)   
 [Примеры кода объекты данных ActiveX (MD)](./ado-md-code-examples.md)   
 [объекты данных ActiveX (MD) коллекции](./ado-md-collections.md)   
 [объекты данных ActiveX (MD) перечислимые константы](./ado-md-enumerated-constants.md)   
 [Методы объекты данных ActiveX (MD)](./ado-md-methods.md)   
 [Объектная модель объекты данных ActiveX (MD)](./ado-md-object-model.md)   
 [Многомерные объекты ADO](./ado-md-objects.md)