---
title: Элемент OnlineIndexOperation (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80cadf48157207cd5aded87c46d29cdd0a85e639
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
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
  
|Характеристика|Description|  
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
  
  
