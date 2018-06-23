---
title: Элемент DataType (ASSL) | Документы Microsoft
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
- DataType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 706d13e68b21a71fa9be80bf89fc4f9cdd4c6014
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095101"
---
# <a name="datatype-element-assl"></a>Элемент DataType (ASSL)
  Определяет тип данных связанного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../data-type/dataitem-data-type-assl.md), [мер](../objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значения для элемента `DataType` определяются в перечислении `System.Data.OleDb.OleDbType`. Тем не менее в элементе `DataType` допускаются только значения перечисления, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*BigInt*|64-разрядное целое число со знаком. Этот тип данных соответствует `Int64` в тип данных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework и DBTYPE_I8 типу данных в OLE DB.|  
|*Bool*|Значение типа Boolean. Этот тип данных соответствует типу данных `Boolean` платформы .NET Framework и типу данных DBTYPE_BOOL в OLE DB.|  
|*Валюта*|Значение валюты в диапазоне от -2<sup>63</sup> (или -922,337,203,685,477.5808) до 2<sup>63</sup>-1 (или + 922,337,203,685,477.5807) с точностью до одной десятитысячной денежной единицы. Этот тип данных соответствует типу данных `Decimal` платформы  .NET Framework и типу данных DBTYPE_CY в OLE DB.|  
|*Дата*|Данные о дате, сохраненные в виде числа с плавающей запятой двойной точности. Целая часть числа равна числу дней, прошедшему с 30 декабря 1899 г., а десятичная часть равна части дня. Этот тип данных соответствует типу данных `DateTime` платформы .NET Framework и типу данных DBTYPE_DATE в OLE DB.|  
|*Double*|Число с плавающей запятой двойной точности в диапазоне от -1,79E +308 до 1,79E +308. Этот тип данных соответствует типу данных `Double` платформы  .NET Framework и типу данных DBTYPE_R8 в OLE DB.|  
|*Целочисленный*|32-разрядное целое число со знаком. Этот тип данных соответствует типу данных `Int32` платформы  .NET Framework и типу данных DBTYPE_I4 в OLE DB.|  
|*Один*|Число с плавающей запятой одинарной точности в диапазоне от -3,40E +38 до 3,40E +38. Этот тип данных соответствует типу данных `Single` платформы  .NET Framework и типу данных DBTYPE_R4 в OLE DB.|  
|*SmallInt*|16-разрядное целое число со знаком. Этот тип данных соответствует типу данных `Int16` платформы  .NET Framework и типу данных DBTYPE_I2 в OLE DB.|  
|*TinyInt*|8-разрядное число со знаком. Этот тип данных соответствует типу данных `SByte` платформы  .NET Framework и типу данных DBTYPE_I4 в OLE DB.|  
|*UnsignedBigInt*|64-разрядное целое число без знака. Этот тип данных соответствует типу данных `UInt64` платформы  .NET Framework и типу данных DBTYPE_UI8 в OLE DB.|  
|*UnsignedInt*|32-разрядное целое число без знака. Этот тип данных соответствует типу данных `UInt32` платформы  .NET Framework и типу данных DBTYPE_UI4 в OLE DB.|  
|*UnsignedSmallInt*|16-разрядное целое число без знака. Этот тип данных соответствует типу данных `UInt16` платформы  .NET Framework и типу данных DBTYPE_UI2 в OLE DB.|  
|*Тип данных WChar*|Поток символов в кодировке Юникод, заканчивающийся символом NULL. Этот тип данных соответствует типу данных `String` платформы .NET Framework и типу данных DBTYPE_WSTR в OLE DB.|  
|*Унаследованные*|Тип данных `DataItem` содержащихся в [источника](source-element-measure-assl.md) элемент `Measure` элемента. **Примечание:** применимо только к `Measure` элементов.|  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  