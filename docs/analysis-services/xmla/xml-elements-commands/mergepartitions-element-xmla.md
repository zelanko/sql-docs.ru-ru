---
title: Элемент MergePartitions (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 937ea7bb52e1b1ab4be992b5a8415edd51e680a9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573956"
---
# <a name="mergepartitions-element-xmla"></a>Элемент MergePartitions (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Выполняет слияние данных из одной или нескольких исходных секций в целевую секцию, а затем удаляет исходные секции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <MergePartitions>  
      <Sources>...</Sources>  
      <Target>...</Target>  
   </MergePartitions>  
</Command>  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Источники](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md), [цели](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Все ссылки на объекты в элементах **Sources** и **Target** должны указывать на отдельные секции в одной группе мер. В противном случае возникает ошибка.  
  
## <a name="see-also"></a>См. также
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
