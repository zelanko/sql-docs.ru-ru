---
title: Элемент WritebackTableCreation (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e04f44d9caa3ae51ea141997e83de54524000fee
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576856"
---
# <a name="writebacktablecreation-element-xmla"></a>Элемент WritebackTableCreation (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет, создается ли таблица обратной записи во время [процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Процесс](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о параметрах обработки, доступных для объектов в экземпляре служб Analysis Services см. в разделе [обработка многомерной модели &#40;служб Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Значением элемента **WritebackTableCreation** может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Создание*|Создает таблицу обратной записи, если она не существует. Если таблица обратной записи уже существует, возвращается ошибка.|  
|*Всегда создавать*|Создает таблицу обратной записи, перезаписывая существующую.|  
|*UseExisting*|Использует существующую таблицу обратной записи, если таковая имеется. В противном случае возвращается ошибка.|  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
