---
title: Элемент Translation (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Translation
- microsoft.xml.analysis.translation
- http://schemas.microsoft.com/analysisservices/2003/engine#Translation
helpviewer_keywords:
- Translation element
ms.assetid: ce962d4b-dda9-4a16-a56c-ff7a5275c48a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7dce14aae6cd8df63d0405869b23f71874cff378
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100464"
---
# <a name="translation-element-xmla"></a>Элемент Translation (XML для аналитики)
  Определяет перевод для элемента атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Translations>  
   ...  
   <Translation>  
      <Language>...</Language>  
      <Name>...</Name>  
   </Translation>  
   ...  
</Translations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Преобразования](translations-element-xmla.md)|  
|Дочерние элементы|[Language](language-element-xmla.md), [Name](name-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Объект `Translation` определяет сведения, необходимые для связи элемента атрибута с переводом, определенным для данного атрибута, во время [вставить](../xml-elements-commands/insert-element-xmla.md) или [обновления](../xml-elements-commands/update-element-xmla.md) команды.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
