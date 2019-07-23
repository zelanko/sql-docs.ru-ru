---
title: Элемент секционирования (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9b7114d3c2efe53bd14028e1b326bd90434ff2e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68034582"
---
# <a name="partitioning-element-dta"></a>Элемент Partitioning (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Содержит схему секционирования, которую должен использовать помощник по настройке ядра СУБД во время анализа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <Partitioning>...</Partitioning>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, без ограничения длины|  
|**Допустимые значения**|**NONE**<br /> Нет секционирования<br /><br /> **ПОЛНОЕ**<br /> Полное секционирование (повышает производительность)<br /><br /> **ALIGNED**<br /> Только секционирование с выравниванием (улучшает управляемость)<br /><br /> С этим элементом следует использовать только одно из данных значений.<br /><br /> Значение**ALIGNED** указывает, что в рекомендациях, созданных помощником по настройке ядра СУБД, каждый предлагаемый индекс будет секционирован точно так же, как и базовая таблица, для которой определяется этот индекс. Некластеризованные индексы в индексированном представлении выравниваются по индексированному представлению.|  
|**Значение по умолчанию**|**NONE**|  
|**Наличие**|Данный элемент должен быть указан один раз в элементе **TuningOptions** , если не используется элемент **DropOnlyMode** . Если используется элемент **DropOnlyMode** , элемент **Partitioning**нельзя использовать. Эти элементы являются взаимоисключающими.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
