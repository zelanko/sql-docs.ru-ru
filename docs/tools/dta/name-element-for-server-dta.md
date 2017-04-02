---
title: "Элемент Name описания сервера (DTA) | Microsoft Docs"
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
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Элемент Name описания сервера (DTA)
  Содержит имя сервера, на котором расположены базы данных, подлежащие настройке.  
  
## Синтаксис  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого элемента **Server** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Server (DTA)](../../tools/dta/server-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## Пример  
 Пример использования этого элемента **Name** см. в статье [Элемент сервера (DTA)](../../tools/dta/server-element-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  