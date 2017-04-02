---
title: "Элемент Table описания схемы (DTA) | Microsoft Docs"
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
  - "Table, элемент [DTA]"
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Элемент Table описания схемы (DTA)
  Указывает таблицу для настройки.  
  
## Синтаксис  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## Атрибуты элемента  
  
|Attribute|Описание|  
|---------------|-----------------|  
|**NumberOfRows**|Необязательно. Целое число, позволяющее имитировать таблицы различных размеров.|  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Необязательно. Перечисляет необходимое число таблиц для рабочей нагрузки.|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Schema описания базы данных (DTA)](../../tools/dta/schema-element-for-database-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания таблицы (DTA)](../../tools/dta/name-element-for-table-dta.md)|  
  
## Замечания  
 Если элемент **Table** не указан, помощник по настройке ядра СУБД считает все таблицы в указанной базе данных доступными для настройки.  
  
## Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  