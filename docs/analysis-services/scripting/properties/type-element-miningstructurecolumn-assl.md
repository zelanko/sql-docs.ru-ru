---
title: Введите элемент (MiningStructureColumn) (ASSL) | Документы Microsoft
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
- Type Element (MiningStructureColumn)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edbbd08e5086157866ff5738d171614925c681cb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-miningstructurecolumn-assl"></a>Элемент Type (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит тип [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Long*|64-разрядное целое число со знаком. Этот тип данных соответствует **Int64** в тип данных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework и DBTYPE_I8 типу данных в OLE DB.|  
|*Логическое значение*|Значение типа Boolean. Этот тип данных соответствует **логическое** тип данных в платформе .NET Framework и типу данных DBTYPE_BOOL в OLE DB.|  
|*Текст*|Поток символов в кодировке Юникод, заканчивающийся символом NULL. Этот тип данных соответствует **строка** тип данных в платформе .NET Framework и типу данных DBTYPE_WSTR в OLE DB.|  
|*Double*|Число с плавающей запятой двойной точности в диапазоне от -1,79E +308 до 1,79E +308. Этот тип данных соответствует **двойные** тип данных в платформе .NET Framework и типу данных DBTYPE_R8 в OLE DB.|  
|*Дата*|Данные о дате, сохраненные в виде числа с плавающей запятой двойной точности. Целая часть числа равна числу дней, прошедшему с 30 декабря 1899 г., а десятичная часть равна части дня. Этот тип данных соответствует **DateTime** тип данных в платформе .NET Framework и типу данных DBTYPE_DATE в OLE DB.|  
|*Таблица*|Вложенная таблица. Этот тип данных соответствует типу данных DBTYPE_HCHAPTER в OLE DB.<br /><br /> Примечание: Столбцы таблицы в .NET Framework нет эквивалентного внутреннего типа данных, но вместо этого поддерживается **DataReader** класса.|  
  
 Перечисление, соответствующее разрешенным значениям для **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 Элемент, соответствующий родителю параметра **тип** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
