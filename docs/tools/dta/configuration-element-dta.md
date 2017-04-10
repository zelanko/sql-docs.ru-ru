---
title: "Элемент Configuration (DTA) | Microsoft Docs"
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
  - "Configuration, элемент"
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# Элемент Configuration (DTA)
  Задает определенную пользователем конфигурацию, состоящую из существующих и гипотетических структур физического проектирования и позволяющую помощнику по настройке ядра СУБД производить анализ при настройке рабочей нагрузки.  
  
## Синтаксис  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## Атрибуты элемента  
  
|Атрибут конфигурации|Описание|  
|-----------------------------|-----------------|  
|**SpecificationMode**|Необязательно. Указывает, должен ли помощник по настройке ядра СУБД анализировать указанную конфигурацию как связь с текущей существующей конфигурацией либо как совершенно новую, отдельную конфигурацию. Используйте тип данных **string** для указания этого атрибута при помощи следующих допустимых значений:<br /><br /> **Relative**:<br />                  Вычисляет указанную конфигурацию как связь с существующей конфигурацией структур физического проектирования (индексы, индексированные представления, секционирование) в настраиваемой базе данных. Например:<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  Вычисляет указанную конфигурацию как самостоятельную. Если указано «Absolute», помощник по настройке ядра СУБД не учитывает существующую конфигурацию. Например:<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Необязательно. Может использоваться один раз для каждого элемента **DTAInput** .|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент DTAInput (DTA)](../../tools/dta/dtainput-element-dta.md)|  
|**Дочерние элементы**|[Элемент Server описания конфигурации (DTA)](../../tools/dta/server-element-for-configuration-dta.md)|  
  
## Пример  
 Пример использования этого элемента см. в статье [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  