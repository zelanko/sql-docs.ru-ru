---
title: Тип данных ColumnBinding (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ColumnBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnBinding
helpviewer_keywords:
- ColumnBinding data type
ms.assetid: 3ab1bac1-6716-4b17-a107-d5f9c744c5e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 271b4ae8b305e554f94bd1b0da3bbed96a7dd476
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149344"
---
# <a name="columnbinding-data-type-assl"></a>Тип данных ColumnBinding (ASSL)
  Определяет производный тип данных, представляющий привязку столбца в представлении источника данных для [DataItem](dataitem-data-type-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ColumnBinding>  
   <!-- The following elements extend Binding -->  
   <TableID>...</TableID>  
      <ColumnID>...</ColumnID>  
</ColumnBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[ColumnID](../properties/columnid-element-eventcolumn-assl.md), [TableID](../properties/id-element-assl.md)|  
|Производные элементы|См. в разделе [привязки](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Чтобы создать допустимые имена элементов XML, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] `DataSet` объектов имена таблиц кодируются как происходит их сериализация для определения схемы XML (XSD); например, имя «Order Details» преобразуется в «Order_x0020_Details». Аналогичным образом в процессе сериализации должно также выполняться кодирование имен элементов `ColumnID` и `TableID`, содержащихся в элементе `ColumnBinding` и ссылающихся на объекты в представлении источника данных, чтобы обеспечить прямую согласованность этих имен с текстом в представлении источника данных. Эти имена декодируются в экземпляре службы Analysis Services по такому же принципу, как и в модели объектов `DataSet`.  
  
 Элемент `TableDefinitions`, содержащийся в элементе с помощью типа данных `TableBinding` и ссылающийся на таблицы в представлении источника данных, также должен выполнять кодирование имен по аналогии с тем, как происходит их сериализация для определения XSD. Однако имена таблиц в связываниях `Partition` не должны быть закодированы, поскольку эти имена являются просто именами таблиц, существующих в базе данных, и не должны находиться в представлении источника данных. Отказ от кодирования имен таблиц в связываниях `Partition` позволяет также достигнуть следующего.  
  
-   Библиотека определения данных для секций становится проще.  
  
-   Обеспечивается большая согласованность, поскольку секции могут содержать либо имена таблиц, либо инструкции SELECT, а инструкции SELECT не должны быть закодированы.  
  
 Имена таблиц и имена столбцов не содержат разделителей (например «[» для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
 Дополнительные сведения о `Binding` типа, включая таблицы объектов языка сценариев служб Analysis Services (ASSL) типа `Binding` тип и иерархию наследования `Binding` типов, см. в разделе [типа привязки данных &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Обзор привязки данных в языке ASSL, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Соответствующим элементом в модели объектов AMO является <xref:Microsoft.AnalysisServices.ColumnBinding>.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
