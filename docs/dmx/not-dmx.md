---
title: "НЕ (DMX) | Документы Microsoft"
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
- NOT
dev_langs:
- DMX
helpviewer_keywords:
- NOT operator [DMX]
ms.assetid: 6d91b3d9-270c-4a68-b41f-169cff5faa0e
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 947d066f9dd13d7f4af15407987fcf218c275cc2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="not-dmx"></a>NOT (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Логический оператор, выполняющий логическое отрицание числового выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Параметры  
 *Expression1*  
 Допустимое выражение расширений интеллектуального анализа данных, возвращающее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение возвращает значение FALSE, если аргумент возвращает значение TRUE, и TRUE в противном случае.  
  
## <a name="remarks"></a>Замечания  
 Аргумент логическим значением (0 — FALSE; любое ненулевое значение — TRUE), прежде чем оператор выполнит логическое отрицание. Если *Expression1* имеет значение TRUE, оператор возвращает FALSE. Если *Expression1* имеет значение FALSE, оператор возвращает TRUE. В следующей таблице иллюстрируется выполнение логического умножения (конъюнкции).  
  
|Если Expression1 равно|Возвращается значение|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Логические операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-logical.md)   
 [Операторы &#40; расширений интеллектуального анализа данных &#41;](../dmx/operators-dmx.md)  
  
  

