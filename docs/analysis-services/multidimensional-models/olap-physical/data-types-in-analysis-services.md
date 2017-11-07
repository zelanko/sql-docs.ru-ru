---
title: "Типы данных в службах Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2310fea62e066c6ad2611a21a8afad3cd48203d4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-types-in-analysis-services"></a>Типы данных в службах Analysis Services
  Для всех <xref:Microsoft.AnalysisServices.DataItem> объектов, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает следующее подмножество **System.Data.OleDb.OleDbType**. Чтобы задать или прочитать тип данных, используйте [DataItem, тип данных &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
## <a name="supported-data-types"></a>Поддерживаемые типы данных  
  
|||  
|-|-|  
|BigInt|64-разрядное целое число со знаком. *BigInt* тип значения представляет целые числа со значениями от отрицательного числа 9223372036854775808 до 9223372036854775807 положительным.|  
|Двоичный|Поток двоичных данных **байтов** типа. **Байтов** является типом значения, представляющий целых чисел без знака со значениями в диапазоне от 0 до 255.|  
|Логическое значение|Экземпляры этого типа имеют значения либо **true** или **false**.|  
|Измерение валют|Объект *валюты* значение в диапазоне от -922,337,203,685,477.5808 до + 922,337,203,685,477.5807 с точностью до одной десятитысячной единицы валюты (четыре десятичных разряда).|  
|Дата|Данные даты и времени, хранящиеся в виде типа double. Целая часть числа равна числу дней, прошедшему с 30 декабря 1899 г., а десятичная часть представляет долю (время) дня.|  
|Double|Число с плавающей запятой в диапазоне от -1,79769313486232E +308 до 1,79769313486232E +308. Значения типа Double хранят сведения о числах с точностью до 15 десятичных знаков после запятой.|  
|Целочисленный|32-разрядное целое число со знаком в диапазоне от минус 2 147 483 648 до плюс 2 147 483 647.|  
|Один|Число с плавающей запятой в диапазоне от - 3,4028235E +38 до 3,4028235E +38. Значения типа Single хранят сведения о числах с точностью до 7 десятичных знаков после запятой.|  
|Smallint|16-разрядное целое число со знаком. *Smallint* тип значения представляет целые числа со знаком со значениями в диапазоне от минус 32768 до плюс 32767.|  
|Tinyint|8-разрядное число со знаком. Значения типа Tinyint представляют целые числа со значениями от минус 128 до плюс 127.|  
|UnsignedBigInt|64-разрядное целое число без знака. *UnsignedBigInt* тип значения представляет целые числа без знака в диапазоне от 0 до 18446744073709551615.|  
|UnsignedInt|32-разрядное целое число без знака. *UnsignedInt* тип значения представляет целых чисел без знака со значениями от 0 до 4 294 967 295.|  
|UnsignedSmallInt|16-разрядное целое число без знака. *UnsignedSmallInt* тип значения представляет целые числа без знака в диапазоне от 0 до 65535.|  
|UnsignedTinyInt|8-разрядное целое число без знака. *UnsignedTinyInt* тип значения представляет целых чисел без знака со значениями в диапазоне от 0 до 255.|  
|WChar|Поток символов в кодировке Юникод, заканчивающийся символом NULL. Объект *WChar* представляет собой последовательный набор знаков Юникода, который используется для представления текста.|  
  
## <a name="amo-validations-on-data-types"></a>Проверки объектов AMO для типов данных  
 В следующей таблице перечислены дополнительные проверки, которые объекты AMO выполняют для определенных привязок.  
  
|Объект|Binding|Допустимые типы данных|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Все, кроме Binary|  
||NameColumn|Только WChar|  
||SkippedLevelsColumn|Только целочисленные типы: BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
||CustomRollupColumn|Только WChar|  
||CustomRollupPropertiesColumn|Только WChar|  
||UnaryOperatorColumn|Только WChar|  
||ValueColumn|все|  
|AttributeTranslation|CaptionColumn|Только WChar|  
|ScalarMiningStructureColumn|KeyColumns|Все, кроме Binary|  
||NameColumn|Только WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|Все, кроме Binary|  
|MeasureGroupAttribute|KeyColumns|Все, кроме Binary|  
|Мера числа различных объектов|Source|BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
  
  

