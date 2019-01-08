---
title: Элемент FeatureSet (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a4bf6fac03eab1e096c0ac5dc63285c11bd3f114
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754476"
---
# <a name="featureset-element-dta"></a>Элемент FeatureSet (DTA)
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
|**Тип данных и длина**|`string`, без ограничения длины|  
|**Допустимые значения**|**IDX_IV**<br /> Индексы и индексированные представления.<br /><br /> **IDX**<br /> Только индексы.<br /><br /> **IV**<br /> Только индексированные представления.<br /><br /> **NCL_IDX**<br /> Только некластеризованные индексы.<br /><br /> Используйте с данным элементом одно из этих значений.|  
|**Значение по умолчанию**|**IDX**|  
|**Наличие**|Требуется для каждого элемента `TuningOptions`, если не используется элемент `DropOnlyMode`. Если используется элемент `DropOnlyMode`, элемент `FeatureSet` нельзя использовать. Эти элементы являются взаимоисключающими.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](tuningoptions-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
