---
title: Элемент FeatureSet (DTA)
description: В программе dta элемент FeatureSet содержит структуры физической конструкции, которые помощник по настройке ядра СУБД использует во время анализа.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 1b14578483eca7160cc810ff6bb7e2f04c0638c0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826508"
---
# <a name="featureset-element-dta"></a>Элемент FeatureSet (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Содержит структуры физического проектирования (индексы или индексированные представления), которые помощник по настройке ядра СУБД должен использовать во время анализа.  
  
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
  
  
