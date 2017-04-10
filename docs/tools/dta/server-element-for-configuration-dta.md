---
title: "Элемент Server описания конфигурации (DTA) | Microsoft Docs"
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
  - "Server, элемент"
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Элемент Server описания конфигурации (DTA)
  Содержит сведения идентификации сервера, на котором помощник по настройке ядра СУБД должен произвести оценку гипотетической конфигурации (заданной элементом **Configuration**).  
  
## Синтаксис  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз на каждый элемент **Configuration** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Configuration (DTA)](../../tools/dta/configuration-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания сервера (DTA)](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Элемент Database описания конфигурации (DTA)](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## Замечания  
 Вы можете указать только один элемент **Server** для элемента **Configuration** . Этот элемент с именем **ServerTypecomplexType** определен в [схеме XML помощника по настройке ядра СУБД](http://go.microsoft.com/fwlink/?linkid=43100). Не следует путать данный элемент **Server** с дочерним элементом элемента **DTAInput** . Дополнительные сведения см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## Пример  
 Пример использования см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  