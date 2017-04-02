---
title: "Элемент DTAInput (DTA) | Microsoft Docs"
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
  - "DTAInput, элемент"
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Элемент DTAInput (DTA)
  Содержит определение входных XML-данных для помощника по настройке ядра СУБД.  
  
## Синтаксис  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## Характеристики элемента  
  
|Характеристики|Описание|  
|---------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Может быть при необходимости указан один раз для каждого элемента **DTAXML** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAXML (DTA)](../../tools/dta/dtaxml-element-dta.md)|  
|**Дочерние элементы**|[Элемент Server (DTA)](../../tools/dta/server-element-dta.md)<br /><br /> [Элемент Workload (DTA)](../../tools/dta/workload-element-dta.md)<br /><br /> [Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Элемент Configuration (DTA)](../../tools/dta/configuration-element-dta.md)|  
  
## Замечания  
 Этот элемент является корневым в иерархии входной схемы помощника по настройке ядра СУБД. С помощью входных аргументов помощника по настройке ядра СУБД можно задавать серверы с подлежащими настройке базами данных, рабочие нагрузки, параметры настройки или пользовательскую конфигурацию.  
  
## Пример  
 Пример использования элемента **DTAInput** см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  