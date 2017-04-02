---
title: "Элемент Name описания базы данных (DTA) | Microsoft Docs"
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
ms.assetid: e871c4fa-3b57-46cf-b4f8-e3be86f92dc4
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Элемент Name описания базы данных (DTA)
  Задает имя базы данных, подлежащей настройке.  
  
## Синтаксис  
  
```  
  
<Server>  
    <Database>  
        <Name>...</Name>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз на каждый элемент **Database** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Database описания сервера (DTA)](../../tools/dta/database-element-for-server-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## Пример  
 Пример использования этого элемента см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  