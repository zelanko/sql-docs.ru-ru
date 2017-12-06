---
title: "Элемент FeatureSet (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4b31e99ca6ad7d26ae67bd3092295cc7736d1fa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="featureset-element-dta"></a>Элемент FeatureSet (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Содержит структуры физического проектирования (индексы или индексированные представления), которые вы хотите использовать во время анализа помощник по настройке ядра СУБД.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, без ограничения длины|  
|**Допустимые значения**|**IDX_IV**<br /> Индексы и индексированные представления.<br /><br /> **IDX**<br /> Только индексы.<br /><br /> **IV**<br /> Только индексированные представления.<br /><br /> **NCL_IDX**<br /> Только некластеризованные индексы.<br /><br /> Используйте с данным элементом одно из этих значений.|  
|**Значение по умолчанию**|**IDX**|  
|**Наличие**|Требуется для каждого элемента **TuningOptions** , если не используется элемент **DropOnlyMode** . Если используется элемент **DropOnlyMode** , элемент **FeatureSet**нельзя использовать. Эти элементы являются взаимоисключающими.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
