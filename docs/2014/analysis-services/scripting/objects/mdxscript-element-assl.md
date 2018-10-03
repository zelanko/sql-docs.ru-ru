---
title: Элемент MdxScript (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MdxScript Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MdxScript
helpviewer_keywords:
- MdxScript element
ms.assetid: 0c59a550-dc95-4d50-948a-bb99348bdd86
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1e138b4112a96bc6cdd5e08af0dbd0941a422d8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106534"
---
# <a name="mdxscript-element-assl"></a>Элемент MdxScript (ASSL)
  Содержит сведения о скрипте многомерных выражений (MDX), с которым связан [куба](cube-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MdxScripts>  
   <MdxScript>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Annotations>...</Annotations>  
      <Commands>...</Commands>  
      <DefaultScript>...</DefaultScript>  
      <CalculationProperties>...</CalculationProperties>  
   </MdxScript>  
</MdxScripts>  
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
|Родительские элементы|[Сценарии многомерных выражений](../collections/mdxscripts-element-assl.md)|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [CalculationProperties](../collections/calculationproperties-element-assl.md), [команды](../collections/commands-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultScript](../properties/defaultscript-element-assl.md), [Описание](../properties/description-element-assl.md), [идентификатор](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [имя](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент скрипта `DefaultScript` по умолчанию имеет значение `True`. Установка значения `DefaultScript` для параметра `True` любого скрипта приводит к установке значения `DefaultScript` для параметра `False` всех других скриптов.  
  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.MdxScript>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
