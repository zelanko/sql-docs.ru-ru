---
title: Элемент Exception (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Exception Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 33af06aa3243b0860bca6d9ae8ff15595ae1ad4f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156815"
---
# <a name="exception-element-xmla"></a>Элемент Exception (XML для аналитики)
  Указывает, что исключение было возвращено из [Discover](../xml-elements-methods-discover.md) или [Execute](../xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** http://schemas.microsoft.com/analysisservices/2003/exception  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[корневой](root-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если во время выполнения метода `Discover` или отдельной команды XMLA при вызове метода `Execute` возникает ошибка, препятствующая завершению команды или метода, элемент `root` для этого метода или команды содержит элемент `Exception` и элемент `Messages`. Элемент `Exception` указывает на ошибку, вследствие которой метод или команда завершилась неудачей, а элемент `Messages` содержит список ошибок или предупреждений, связанных с этой ошибкой.  
  
## <a name="see-also"></a>См. также  
 [Сообщения элемент &#40;XML для Аналитики&#41;](messages-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
