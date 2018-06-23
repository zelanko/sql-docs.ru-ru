---
title: Элемент языка (XMLA) | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Language Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Language
- microsoft.xml.analysis.language
- http://schemas.microsoft.com/analysisservices/2003/engine#Language
helpviewer_keywords:
- Language element
ms.assetid: cd998202-e43f-4c6c-8727-a15a76a520ea
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5ea8c37369c45d35a8fe3c7366c2d5293e0c48a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099864"
---
# <a name="language-element-xmla"></a>Элемент Language (XML для аналитики)
  Содержит идентификатор языка (LCID) для родительского [перевода](translation-element-xmla.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Translation>  
   ...  
   <Language>...</Language>  
   ...  
</Translation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Перевод](translation-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Language` указывает код языка, используемый родительским элементом `Translation` для назначения элемента `Name` родительского элемента `Translation` на указанном языке элементу атрибута во время выполнения команды `Insert` или `Update`.  
  
## <a name="see-also"></a>См. также  
 [Элемент INSERT &#40;XML для Аналитики&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Элемент Name &#40;XML для Аналитики&#41;](name-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  