---
title: "Элемент Schema описания базы данных (DTA) | Microsoft Docs"
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
  - "Schema, элемент"
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Элемент Schema описания базы данных (DTA)
  Указывает схему базы данных, которую необходимо настроить.  
  
## Синтаксис  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для элемента **Database** , указанного в элементе **Server** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Database для сервера (DTA)](../../tools/dta/database-element-for-server-dta.md)|  
|**Дочерние элементы**|[Элемент Name для схемы (DTA)](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Элемент Table для схемы (DTA)](../../tools/dta/table-element-for-schema-dta.md)|  
  
## Пример  
 Пример использования этого элемента см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  