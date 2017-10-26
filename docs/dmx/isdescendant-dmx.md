---
title: "IsDescendant (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsDescendant
dev_langs:
- DMX
helpviewer_keywords:
- IsDescendant function
ms.assetid: d9fe7446-edb5-487b-8ea6-c9efaccf6d90
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4a1e7959a303b768851784af0ab9c88abd257674
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="isdescendant-dmx"></a>IsDescendant (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает, является ли текущий узел потомком заданного узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип Boolean.  
  
## <a name="remarks"></a>Замечания  
 **IsDescendant** используется только в [SELECT FROM &#60; модели &#62;. СОДЕРЖИМОЕ &#40; расширений интеллектуального анализа данных &#41; ](../dmx/select-from-model-content-dmx.md) и [SELECT FROM &#60; модели &#62;. DIMENSION_CONTENT &#40; расширений интеллектуального анализа данных &#41; ](../dmx/select-from-model-dimension-content-dmx.md) запросов.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере выдаются все объекты, которые являются потомками узла, заданного в функции IsDescendant.  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40; расширений интеллектуального анализа данных &#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40; расширений интеллектуального анализа данных &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

