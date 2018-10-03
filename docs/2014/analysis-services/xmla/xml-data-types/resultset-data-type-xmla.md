---
title: Тип данных ResultSet (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Resultset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a34b99aa63608faafa42d94aaf8938f86bb3894c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205494"
---
# <a name="resultset-data-type-xmla"></a>Тип данных Resultset (XML для аналитики)
  Определяет абстрактный примитивный тип данных, представляющий данные, возвращенные из [Discover](../xml-elements-methods-discover.md) или [Execute](../xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis:resultset  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|None|  
|Производные типы данных|[MDDataSet](mddataset-data-type-xmla.md), [olapxmla_EmptyResult](emptyresult-data-type-xmla.md), [набора строк](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[Исключение](../xml-elements-properties/exception-element-xmla.md), [сообщений](../xml-elements-properties/messages-element-xmla.md)|  
|Производные элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Тип данных `Resultset` представляет собой описывающий сам себя результирующий набор XML, который может включать и схему, и данные, в зависимости от типа возвращаемых данных.  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types-xmla.md)  
  
  
