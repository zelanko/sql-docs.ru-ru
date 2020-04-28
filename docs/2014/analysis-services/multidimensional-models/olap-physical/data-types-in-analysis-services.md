---
title: Типы данных в Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ecdc64918e582f25f0e017d263c66e78c0d1bee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62725388"
---
# <a name="data-types-in-analysis-services"></a>Типы данных в службах Analysis Services
  Для всех <xref:Microsoft.AnalysisServices.DataItem> объектов [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживает следующее подмножество `System.Data.OleDb.OleDbType`. Чтобы задать или прочитать тип данных, используйте [тип данных dataitem &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/data-type/dataitem-data-type-assl).  
  
## <a name="supported-data-types"></a>Поддерживаемые типы данных  
  
|||  
|-|-|  
|BigInt|64-разрядное целое число со знаком. Тип значения *bigint* представляет целые числа со значениями от минус до 9223372036854775808 до положительного 9 223 372 036 854 775 807.|  
|Двоичные данные|Поток двоичных данных типа **Byte** . **Byte** — это тип значения, представляющий целые числа без знака со значениями в диапазоне от 0 до 255.|  
|Логическое|Экземпляры этого типа имеют значения либо `true`, либо `false`.|  
|Валюта|Значение *валюты* от-922 337 203 685 477,5808 до + 922 337 203 685 477,5807 с точностью до одной десятитысячной единицы валюты (четыре десятичные разряды).|  
|Дата|Данные даты и времени, хранящиеся в виде типа double. Целая часть числа равна числу дней, прошедшему с 30 декабря 1899 г., а десятичная часть представляет долю (время) дня.|  
|Double|Число с плавающей запятой в диапазоне от -1,79769313486232E +308 до 1,79769313486232E +308. Значения типа Double хранят сведения о числах с точностью до 15 десятичных знаков после запятой.|  
|Целое число|32-разрядное целое число со знаком в диапазоне от минус 2 147 483 648 до плюс 2 147 483 647.|  
|Один|Число с плавающей запятой в диапазоне от - 3,4028235E +38 до 3,4028235E +38. Значения типа Single хранят сведения о числах с точностью до 7 десятичных знаков после запятой.|  
|Smallint|16-разрядное целое число со знаком. Тип значения *smallint* представляет целые числа со знаком со значениями от отрицательного 32768 до положительного 32767.|  
|Tinyint|8-разрядное число со знаком. Значения типа Tinyint представляют целые числа со значениями от минус 128 до плюс 127.|  
|UnsignedBigInt|64-разрядное целое число без знака. Тип значения *UnsignedBigInt* представляет целые числа без знака со значениями от 0 до 18446744073709551615.|  
|UnsignedInt|32-разрядное целое число без знака. Тип значения *unsignedInt* представляет целые числа без знака со значениями от 0 до 4 294 967 295.|  
|UnsignedSmallInt|16-разрядное целое число без знака. Тип значения *UnsignedSmallInt* представляет целые числа без знака со значениями от 0 до 65535.|  
|UnsignedTinyInt|8-разрядное целое число без знака. Тип значения *UnsignedTinyInt* представляет целые числа без знака со значениями в диапазоне от 0 до 255.|  
|WChar|Поток символов в кодировке Юникод, заканчивающийся символом NULL. *WCHAR* — это последовательная коллекция символов Юникода, используемая для представления текста.|  
  
## <a name="amo-validations-on-data-types"></a>Проверки объектов AMO для типов данных  
 В следующей таблице перечислены дополнительные проверки, которые объекты AMO выполняют для определенных привязок.  
  
|Объект|Привязка|Допустимые типы данных|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Все, кроме Binary|  
||NameColumn|Только WChar|  
||SkippedLevelsColumn|Только целочисленные типы: BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
||CustomRollupColumn|Только WChar|  
||CustomRollupPropertiesColumn|Только WChar|  
||UnaryOperatorColumn|Только WChar|  
||ValueColumn|All|  
|AttributeTranslation|CaptionColumn|Только WChar|  
|ScalarMiningStructureColumn|KeyColumns|Все, кроме Binary|  
||NameColumn|Только WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|Все, кроме Binary|  
|MeasureGroupAttribute|KeyColumns|Все, кроме Binary|  
|Мера числа различных объектов|Источник|BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
  
  
