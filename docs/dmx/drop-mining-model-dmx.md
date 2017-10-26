---
title: "УДАЛЕНИЕ МОДЕЛИ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ (DMX) | Документы Microsoft"
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
- DROP_MINING_MODEL
dev_langs:
- DMX
helpviewer_keywords:
- DROP MINING MODEL statement
- deleting mining models
- removing mining models
- dropping mining models
- mining models [Analysis Services], deleting
ms.assetid: 8ff561d0-a526-4712-9fff-11df9f8c45a1
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 450ce17816858d1ba35ff8da77d15c44140b4f17
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="drop-mining-model-dmx"></a>DROP MINING MODEL (расширения интеллектуального анализа данных)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет модель интеллектуального анализа данных из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP MINING MODEL <model >  
```  
  
## <a name="arguments"></a>Аргументы  
 *model*  
 Идентификатор модели.  
  
## <a name="examples"></a>Примеры  
 Следующий образец кода удаляет модель интеллектуального анализа данных NBSample.  
  
```  
DROP MINING MODEL [NBSample]  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

