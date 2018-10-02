---
title: Элемент OnlineIndexOperation (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 39bb19b2b0b4c9e7a7dd11d227f1d84536702aa0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796292"
---
# <a name="onlineindexoperation-element-dta"></a>Элемент OnlineIndexOperation (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Указывает, могут ли индексы, индексированные представления или секции, рекомендуемые помощником по настройке ядра СУБД, создаваться в режиме в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, без ограничения длины|  
|**Допустимые значения**|**OFF**<br /> Рекомендованные структуры физического проектирования не могут быть созданы в оперативном режиме.<br /><br /> **ON**<br /> Все рекомендованные структуры физического проектирования могут быть созданы в режиме в сети.<br /><br /> **MIXED**<br /> Помощник по настройке ядра СУБД пытается рекомендовать структуры физического проектирования, которые могут быть созданы, по возможности, в режиме в сети.<br /><br /> Используйте с данным элементом одно из этих значений. Если индексы создаются в режиме в сети, то к их определению объекта добавляется ключевое слово **ONLINE = ON** .|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. В случае использования может быть использован один раз для элемента **TuningOptions** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
