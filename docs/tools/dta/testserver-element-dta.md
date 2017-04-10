---
title: "Элемент TestServer (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "TestServer, элемент"
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Элемент TestServer (DTA)
  Указывает, какой тестовый сервер нужно использовать при настройке рабочего сервера.  
  
## Синтаксис  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Необязательно. Может использоваться один раз для каждого элемента **TuningOptions** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## Пример  
 Пример использования этого элемента см. в разделе [Уменьшение настроечной загрузки рабочего сервера](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  