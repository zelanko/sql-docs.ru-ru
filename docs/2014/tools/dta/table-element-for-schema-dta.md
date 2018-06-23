---
title: Элемент таблицы для схемы (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 44df363381b2811b422f29671fe4902c1dd7c23e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188359"
---
# <a name="table-element-for-schema-dta"></a>Элемент Table описания схемы (DTA)
  Указывает таблицу для настройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|attribute|Описание|  
|---------------|-----------------|  
|`NumberOfRows`|Необязательный параметр. Целое число, позволяющее имитировать таблицы различных размеров.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Перечисляет необходимое число таблиц для рабочей нагрузки.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент schema описания базы данных &#40;DTA&#41;](schema-element-for-database-dta.md)|  
|**Дочерние элементы**|[Элемент Name для таблицы &#40;DTA&#41;](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Примечания  
 Если элемент `Table` не указан, помощник по настройке ядра СУБД считает все таблицы в указанной базе данных доступными для настройки.  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](server-element-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  