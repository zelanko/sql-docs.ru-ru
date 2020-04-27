---
title: Элемент Table для Schema (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8b3a72f800643afa5e7edf6bdfa9928196f5da2d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63138786"
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
  
|attribute|Description|  
|---------------|-----------------|  
|`NumberOfRows`|Необязательный параметр. Целое число, позволяющее имитировать таблицы различных размеров.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**строка**, от 1 до 255 символов.|  
|**Значение по умолчанию**|Отсутствует.|  
|**Однократно**|Необязательный параметр. Перечисляет необходимое число таблиц для рабочей нагрузки.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Schema описания базы данных (DTA)](schema-element-for-database-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания таблицы (DTA)](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Если элемент `Table` не указан, помощник по настройке ядра СУБД считает все таблицы в указанной базе данных доступными для настройки.  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](server-element-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
