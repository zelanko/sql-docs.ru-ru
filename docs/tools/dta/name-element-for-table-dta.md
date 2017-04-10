---
title: "Элемент Name описания таблицы (DTA) | Microsoft Docs"
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
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Элемент Name описания таблицы (DTA)
  Позволяет задать имя настраиваемой таблицы.  
  
## Синтаксис  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Обязательный. Один раз для каждого элемента **Table** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Table для схемы (DTA)](../../tools/dta/table-element-for-schema-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  