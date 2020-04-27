---
title: Элемент Column для index (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef7972014dff498172b9c016b3a7debb79a054fa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63149849"
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
  
|Атрибут столбца|Описание|  
|----------------------|-----------------|  
|`Type`|Необязательный параметр. Указывает тип столбца индекса. Используйте тип данных **string** для указания этого атрибута при помощи следующих допустимых значений:<br /><br /> `KeyColumn`:<br />                  Указывает, что на столбец ссылается ключ индекса. Для установки этого атрибута используйте следующий синтаксис:<br />`<Column Type="KeyColumn">`<br />Дополнительные сведения о ключевых столбцах см. в разделе [Описания кластеризованных и некластеризованных индексов](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).<br /><br /> `IncludedColumn`: Указывает, что столбец является включенным столбцом (а не ключевым столбцом). Для установки этого атрибута используйте следующий синтаксис:<br />`<Column Type="IncludedColumn">`<br />Дополнительные сведения о включенных столбцах см. в разделе [Создание индексов с включенными столбцами](../../relational-databases/indexes/create-indexes-with-included-columns.md).|  
|`SortOrder`|Необязательный параметр. Указывает порядок сортировки столбца. Используйте тип данных **string** для указания порядка сортировки **по возрастанию** или **по убыванию** , как показано ниже:<br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Отсутствует.|  
|**Значение по умолчанию**|Отсутствует.|  
|**Однократно**|Для элемента `Index` можно задать не более 1 024 столбцов.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Index (DTA)](index-element-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания столбца (DTA)](name-element-for-column-dta.md)|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
