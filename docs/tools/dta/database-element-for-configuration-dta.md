---
title: "Элемент Database описания конфигурации (DTA) | Microsoft Docs"
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
  - "Database, элемент"
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Элемент Database описания конфигурации (DTA)
  Задает базу данных, в которой помощник по настройке ядра СУБД будет оценивать гипотетическую конфигурацию (заданную элементом **Configuration**).  
  
## Синтаксис  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один или несколько раз для каждого элемента **Server** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Server описания конфигурации (DTA)](../../tools/dta/server-element-for-configuration-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания базы данных (DTA)](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Элемент Schema описания базы данных (DTA)](../../tools/dta/schema-element-for-database-dta.md)<br /><br /> [Элемент Recommendation (DTA)](../../tools/dta/recommendation-element-dta.md)|  
  
## Замечания  
 Этот элемент с именем **DatabaseTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Не путайте этот элемент **Database** с элементом, родительским корневым элементом которого является элемент **Server** , находящийся в верхней части входного XML-файла. Дополнительные сведения см. в разделе [Элемент Database описания сервера (DTA)](../../tools/dta/database-element-for-server-dta.md).  
  
## Пример  
 Пример использования элемента **Database** см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  