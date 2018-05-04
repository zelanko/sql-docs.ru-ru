---
title: ОБНОВЛЕНИЕ (ДАННЫХ DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- UPDATE
dev_langs:
- DMX
helpviewer_keywords:
- NODE_CAPTION column
- mining models [Analysis Services], content changes
- modifying mining model content
- UPDATE statement [SQL Server], DMX
ms.assetid: 8a2b0942-c490-410c-b1cf-ff2e0fd8e24b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c8b479dc74fe63a9eff4245be64a9eef5429101c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="update-dmx"></a>UPDATE (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Изменения **NODE_CAPTION** столбца в модели интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE <model>.CONTENT  
SET NODE_CAPTION='new caption'  
[WHERE <condition expression>]  
```  
  
## <a name="arguments"></a>Аргументы  
 *model*  
 Идентификатор модели.  
  
 *новый заголовок*  
 Строка, содержащая новое имя для **NODE_CAPTION** столбца.  
  
 *Условное выражение*  
 Необязательно. Условие ограничения значений, возвращаемых из списка столбцов.  
  
## <a name="examples"></a>Примеры  
 В следующем примере **обновление** инструкция изменяет имя по умолчанию `Cluster 1`, для кластера `001` на более описательное имя `Likely Customers`.  
  
```  
UPDATE [TM Clustering].CONTENT  
SET NODE_CAPTION= 'Likely Customers'  
WHERE NODE_UNIQUE_NAME = '001'  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
