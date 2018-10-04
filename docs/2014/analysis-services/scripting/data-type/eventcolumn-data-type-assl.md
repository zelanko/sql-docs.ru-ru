---
title: Тип данных EventColumn (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EventColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventColumn
helpviewer_keywords:
- EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 175504777bdba88ef434d275f136becc8241ada0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118044"
---
# <a name="eventcolumn-data-type-assl"></a>Тип данных EventColumn (ASSL)
  Определяет тип-примитив, представляющий столбец с данными, которые захватываются для [событий](../objects/event-element-assl.md) элемент как часть [трассировки](../objects/trace-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[ColumnID](../properties/columnid-element-eventcolumn-assl.md)|  
|Производные элементы|[Столбец](../objects/column-element-assl.md) ([столбцы](../collections/columns-element-assl.md) коллекцию [трассировки](../objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>См. также  
 [Элемент Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
