---
title: "Элемент File (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "File, элемент"
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Элемент File (DTA)
  Служит для указания файла рабочей нагрузки. Рабочая нагрузка представляет собой набор инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], выполняемый в одной или нескольких базах данных, которые необходимо настроить. Файлы рабочей нагрузки могут представлять собой скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] (SQL) или файлы трассировки (TRC). Дополнительные сведения см. в разделе[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).  
  
## Синтаксис  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Для задания пути к каталогу, в котором находится файл рабочей загрузки, используется тип данных **string** . Например:<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Помните, что ограничение на длину устанавливается сервером.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необходимо наличие одного такого элемента, если не задан никакой другой тип рабочей нагрузки. Для родительского элемента **Workload**необходимо задать дочерний элемент **EventString**, **File** или **Database** , однако одновременно может использоваться только один из них. Например, если рабочая нагрузка задана элементом **File** , то в том же входном XML-файле уже нельзя задать рабочую нагрузку элементом **Database** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Workload (DTA)](../../tools/dta/workload-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  