---
title: "Элемент COLUMN описания индекса (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7aaf1a73356f2e5a2732e12e49b7e618c3bf1f0e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="column-element-for-index-dta"></a>Элемент Column описания индекса (DTA)
  Указывает столбцы, по которым создается индекс для пользовательской конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
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
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Для элемента **Index** можно задать не более 1024 столбцов.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент index &#40; DTA &#41;](../../tools/dta/index-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания столбца &#40; DTA &#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

