---
title: "Элемент Name описания столбца (DTA) | Microsoft Docs"
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
  - "Name, элемент"
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Элемент Name описания столбца (DTA)
  Задает имя для столбца индекса в пользовательской конфигурации.  
  
## Синтаксис  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого элемента **Column** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Column описания индекса (DTA)](../../tools/dta/column-element-for-index-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  