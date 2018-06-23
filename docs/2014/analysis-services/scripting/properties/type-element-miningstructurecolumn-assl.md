---
title: Введите элемент (MiningStructureColumn) (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (MiningStructureColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bac190fcde3dfb4a5e0768e42c7cf0e1b7b6659f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191303"
---
# <a name="type-element-miningstructurecolumn-assl"></a>Элемент Type (MiningStructureColumn) (ASSL)
  Содержит тип [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Long*|64-разрядное целое число со знаком. Этот тип данных соответствует типу данных `Int64` платформы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework и типу данных DBTYPE_I8 в OLE DB.|  
|*Boolean*|Значение типа Boolean. Этот тип данных соответствует типу данных `Boolean` платформы .NET Framework и типу данных DBTYPE_BOOL в OLE DB.|  
|*Текст*|Поток символов в кодировке Юникод, заканчивающийся символом NULL. Этот тип данных соответствует типу данных `String` платформы .NET Framework и типу данных DBTYPE_WSTR в OLE DB.|  
|*Double*|Число с плавающей запятой двойной точности в диапазоне от -1,79E +308 до 1,79E +308. Этот тип данных соответствует типу данных `Double` платформы  .NET Framework и типу данных DBTYPE_R8 в OLE DB.|  
|*Дата*|Данные о дате, сохраненные в виде числа с плавающей запятой двойной точности. Целая часть числа равна числу дней, прошедшему с 30 декабря 1899 г., а десятичная часть равна части дня. Этот тип данных соответствует типу данных `DateTime` платформы .NET Framework и типу данных DBTYPE_DATE в OLE DB.|  
|*Таблица*|Вложенная таблица. Этот тип данных соответствует типу данных DBTYPE_HCHAPTER в OLE DB. **Примечание:** столбцы таблицы в .NET Framework нет эквивалентного внутреннего типа данных, но вместо этого поддерживается `DataReader` класса.|  
  
 Перечисление, соответствующее допустимым значениям элемента `Type` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 Элемент, соответствующий родителю параметра `Type` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  