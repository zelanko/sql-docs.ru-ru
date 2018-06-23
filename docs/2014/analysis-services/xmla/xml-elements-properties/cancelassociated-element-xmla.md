---
title: Элемент CancelAssociated (XML для Аналитики) | Документы Microsoft
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
- CancelAssociated Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancelassociated
- urn:schemas-microsoft-com:xml-analysis#CancelAssociated
- http://schemas.microsoft.com/analysisservices/2003/engine#CancelAssociated
helpviewer_keywords:
- CancelAssociated element
ms.assetid: fd890440-d1a7-4c05-9e81-c81e6b8c274c
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1e747815b30daf86edff4ad976d6fb5370bf9c3b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195005"
---
# <a name="cancelassociated-element-xmla"></a>Элемент CancelAssociated (XML для аналитики)
  Указывает, должен ли родительский элемент [Cancel](../xml-elements-commands/cancel-element-xmla.md) отменить все связанные команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|False|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Отмена](../xml-elements-commands/cancel-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если этот элемент задан и имеет `True`, каждый соответствующие соединения, сеансов и команды, заданные в родительском объекте `Cancel` Команда отменена.  
  
## <a name="see-also"></a>См. также  
 [Элемент ConnectionID &#40;XML для Аналитики&#41;](id-element-xmla.md)   
 [Элемент SessionID &#40;XML для Аналитики&#41;](sessionid-element-xmla.md)   
 [Элемент SPID &#40;XML для Аналитики&#41;](spid-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  