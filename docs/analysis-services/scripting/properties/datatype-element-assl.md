---
title: Элемент DataType (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DataType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c9a45fa75f92d38ab707e31c792cd7e388e1fab2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datatype-element-assl"></a>Элемент DataType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md), [мер](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значения для **DataType** определены в **System.Data.OleDb.OleDbType** перечисления. Тем не менее, допустимы только значения перечисления в следующей таблице в **DataType** элемента.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*BigInt*|64-разрядное целое число со знаком. Этот тип данных соответствует **Int64** в тип данных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework и DBTYPE_I8 типу данных в OLE DB.|  
|*bool*|Значение типа Boolean. Этот тип данных соответствует **логическое** тип данных в платформе .NET Framework и типу данных DBTYPE_BOOL в OLE DB.|  
|*Измерение валют*|Значение валюты в диапазоне от -2<sup>63</sup> (или -922,337,203,685,477.5808) до 2<sup>63</sup>-1 (или + 922,337,203,685,477.5807) с точностью до одной десятитысячной денежной единицы. Этот тип данных соответствует **десятичное** тип данных в платформе .NET Framework и типу данных DBTYPE_CY в OLE DB.|  
|*Дата*|Данные о дате, сохраненные в виде числа с плавающей запятой двойной точности. Целая часть числа равна числу дней, прошедшему с 30 декабря 1899 г., а десятичная часть равна части дня. Этот тип данных соответствует **DateTime** тип данных в платформе .NET Framework и типу данных DBTYPE_DATE в OLE DB.|  
|*Double*|Число с плавающей запятой двойной точности в диапазоне от -1,79E +308 до 1,79E +308. Этот тип данных соответствует **двойные** тип данных в платформе .NET Framework и типу данных DBTYPE_R8 в OLE DB.|  
|*Целочисленный*|32-разрядное целое число со знаком. Этот тип данных соответствует **Int32** тип данных в платформе .NET Framework и типу данных DBTYPE_I4 в OLE DB.|  
|*Один*|Число с плавающей запятой одинарной точности в диапазоне от -3,40E +38 до 3,40E +38. Этот тип данных соответствует **одного** тип данных в .NET Framework и типу данных DBTYPE_R4 в OLE DB.|  
|*SmallInt*|16-разрядное целое число со знаком. Этот тип данных соответствует **Int16** тип данных в платформе .NET Framework и типу данных DBTYPE_I2 в OLE DB.|  
|*TinyInt*|8-разрядное число со знаком. Этот тип данных соответствует **SByte** тип данных в платформе .NET Framework и типу данных DBTYPE_I1 в OLE DB.|  
|*UnsignedBigInt*|64-разрядное целое число без знака. Этот тип данных соответствует **UInt64** тип данных в .NET Framework и типу данных DBTYPE_UI8 в OLE DB.|  
|*UnsignedInt*|32-разрядное целое число без знака. Этот тип данных соответствует **UInt32** тип данных в платформе .NET Framework и типу данных DBTYPE_UI4 в OLE DB.|  
|*UnsignedSmallInt*|16-разрядное целое число без знака. Этот тип данных соответствует **UInt16** тип данных в платформе .NET Framework и типу данных DBTYPE_UI2 в OLE DB.|  
|*Тип данных WChar*|Поток символов в кодировке Юникод, заканчивающийся символом NULL. Этот тип данных соответствует **строка** тип данных в платформе .NET Framework и типу данных DBTYPE_WSTR в OLE DB.|  
|*Унаследованные*|Тип данных **DataItem** содержащихся в [источника](../../../analysis-services/scripting/properties/source-element-measure-assl.md) элемент **мер** элемента.<br /><br /> Примечание: Применимо только к **мер** элементов.|  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
