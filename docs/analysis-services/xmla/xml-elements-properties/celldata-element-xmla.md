---
title: Элемент CellData (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01f1bfbd4565c42f4867a781b8f4502ede3a09f4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="celldata-element-xmla"></a>Элемент CellData (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию элементов Cell, представляющих данные ячеек и содержащиеся в элементе [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) , который использует тип данных [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) .  
  
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
|Родительские элементы|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Дочерние элементы|[Ячейки](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 В родительском корневом элементе, за элементом **Axes** следует элемент **CellData** , коллекция элементов **Cell** , которая содержит значения свойств ячейки для каждой ячейки, возвращенной в многомерном наборе данных.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
