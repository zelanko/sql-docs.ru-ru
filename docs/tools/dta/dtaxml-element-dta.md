---
title: "Элемент DTAXML (DTA) | Microsoft Docs"
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
  - "DTAXML, элемент"
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Элемент DTAXML (DTA)
  **DTAXML** — корневой элемент входного или выходного файла XML-данных помощника по настройке ядра СУБД — содержит все элементы, определяющие вход и выход настройки, создаваемой помощником по настройке ядра СУБД.  
  
## Синтаксис  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## Атрибуты элемента  
  
|Attribute|Описание|  
|---------------|-----------------|  
|**xmlns:xsi**|Обязательный. Определяет пространство имен экземпляра XML-схемы. Атрибуты этого пространства имен используются для обращения к схеме, применяемой для проверки XML-файла помощника по настройке ядра СУБД.<br /><br /> Обязательное значение: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Обязательный. Определяет пространство имен помощника по настройке ядра СУБД.<br /><br /> При редактировании XML-файла помощника по настройке ядра СУБД в редакторе XML из [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]это значение используется в справке F1, а также в динамической справке для поиска подходящих разделов электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Обязательное значение:<br /><br /> [XML-схема помощника по настройке компонента Database Engine](http://go.microsoft.com/fwlink/?LinkId=43100) Пространство имен|  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого файла DTA XML.|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|None|  
|**Дочерние элементы**|[Элемент DTAInput (DTA)](../../tools/dta/dtainput-element-dta.md)<br /><br /> Элемент **DTAOutput** (см. раздел [XML-схема помощника по настройке ядра СУБД](http://schemas.microsoft.com/sqlserver/))|  
  
## Замечания  
 Дополнительные сведения о пространствах имен XML см. в статье [Пространства имен в XML-документе](http://go.microsoft.com/fwlink/?LinkId=7341) в библиотеке [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN.  
  
## Пример  
 Примеры типичных элементов **DTAXML** см. в разделе [Образцы входных XML-файлов (DTA)](../../tools/dta/xml-input-file-samples-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  