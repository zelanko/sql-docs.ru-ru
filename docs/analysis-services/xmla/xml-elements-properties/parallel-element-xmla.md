---
title: Параллельная элемент (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 88e7cf2387c8ee45936b5de21f529e142142d02c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050413"
---
# <a name="parallel-element-xmla"></a>Parallel Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, сколько обработки заданий могут выполняться параллельно, с помощью родительского [пакета](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Batch>  
   ....  
   <Parallel maxParallel="Integer">  
      <!-- An XMLA process command -->  
   </Parallel>  
   ....  
</Batch>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Пакетной службы](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)|  
|Дочерние элементы|[Process, элемент](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|maxParallel|Необязательный атрибут типа **Integer** . Определяет максимальное количество потоков для параллельного выполнения команд. Если не указан или задано значение 0, экземпляр служб Analysis Services определяет оптимальное количество потоков, в зависимости от количества процессоров, доступных на компьютере.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
