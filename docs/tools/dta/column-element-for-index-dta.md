---
title: "Элемент Column описания индекса (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
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
  - "Column, элемент"
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Элемент Column описания индекса (DTA)
  Указывает столбцы, по которым создается индекс для пользовательской конфигурации.  
  
## Синтаксис  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## Атрибуты элемента  
  
 **Type**: необязательно. Указывает тип столбца индекса. Используйте тип данных **string** для указания этого атрибута при помощи следующих допустимых значений:  
  
-   **KeyColumn**  
  
     Указывает, что на столбец ссылается ключ индекса. Для установки этого атрибута используйте следующий синтаксис:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Дополнительные сведения о ключевых столбцах см. в разделе [Описания кластеризованных и некластеризованных индексов](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Указывает, что столбец является включенным (а не ключевым) столбцом. Для установки этого атрибута используйте следующий синтаксис:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Дополнительные сведения о включенных столбцах см. в разделе [Создание индексов с включенными столбцами](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: необязательно. Указывает порядок сортировки столбца. Используйте тип данных **string** для указания порядка сортировки **по возрастанию** или **по убыванию** , как показано ниже:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Для элемента **Index** можно задать не более 1024 столбцов.|  
  
## Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Index (DTA)](../../tools/dta/index-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания столбца (DTA)](../../tools/dta/name-element-for-column-dta.md)|  
  
## Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  