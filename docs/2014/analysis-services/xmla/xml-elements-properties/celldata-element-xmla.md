---
title: Элемент CellData (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CellData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellData
- http://schemas.microsoft.com/analysisservices/2003/engine#CellData
- urn:schemas-microsoft-com:xml-analysis#CellData
- microsoft.xml.analysis.celldata
helpviewer_keywords:
- CellData element
ms.assetid: 0ebfb5e1-a674-4b9b-bd8c-c529da105f61
caps.latest.revision: 27
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: ce445127e78f7f503bf3b81a640047f0d1f1d87f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193453"
---
# <a name="celldata-element-xmla"></a>Элемент CellData (XML для аналитики)
  Содержит коллекцию элементов Cell, представляющих данные ячеек и содержащиеся в элементе [root](root-element-xmla.md) , который использует тип данных [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <CellData>  
      <Cell>...</Cell>  
   </CellData>  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корень](root-element-xmla.md)|  
|Дочерние элементы|[Cell](cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 В родительском корневом элементе, за элементом `Axes` следует элемент `CellData`, коллекция элементов `Cell`, которая содержит значения свойств ячейки для каждой ячейки, возвращенной в многомерном наборе данных.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  