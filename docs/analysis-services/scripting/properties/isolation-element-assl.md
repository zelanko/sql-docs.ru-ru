---
title: Элемент isolation (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Isolation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 740e7eceffa4cbbbc3dcf7fce1059a6140b3feac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="isolation-element-assl"></a>Элемент Isolation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает уровень изоляции для элемента, который является производным от [DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md) тип данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Читать зафиксированные*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Источник данных](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение для этого элемента ограничивается одной из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Читать зафиксированные*|Указывает, что инструкции не могут считывать данные, которые были изменены другими транзакциями, но еще не были зафиксированы. Это предотвращает чтение«грязных» данных. В других транзакциях могут изменяться данные в промежутках времени между выполнением отдельных инструкций в текущей транзакции. Это приводит к появлению таких ошибок, как неповторяющиеся чтение или фантомные данные. Это значение применяется по умолчанию для элемента **Isolation** .|  
|*Моментальный снимок*|Указывает на то, что данные, считанные любой инструкцией транзакции, будут согласованы на уровне транзакции с версией данных, существовавших в ее начале. Транзакция распознает только те изменения в данных, которые были зафиксированы до ее начала. Инструкции, выполняемые текущей транзакцией, не видят изменений данных, произведенных другими транзакциями после запуска текущей транзакции. Таким образом достигается эффект получения инструкциями в транзакции моментального снимка зафиксированных данных на момент запуска транзакции.|  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
