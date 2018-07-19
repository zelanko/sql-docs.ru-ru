---
title: Элемент SynchronizeSecurity (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f99f4c0ddf212d2fac33abd08c33ccf3dbe7998
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046928"
---
# <a name="synchronizesecurity-element-xmla"></a>Элемент SynchronizeSecurity (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Указывает, как синхронизировать определения безопасности, такие как роли и разрешения, во время выполнения [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Synchronize>  
   ...  
   <SynchronizeSecurity>...</SynchronizeSecurity>  
   ...  
</Synchronize>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*SkipMembership*|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 **Безопасности** определяет, синхронизированы ли определения безопасности, такие как роли и разрешения, определенные в базе данных служб Analysis Services во время **Synchronize** команды. Этот элемент также определяет, включаются ли определенные в качестве элементов определений безопасности учетные записи пользователей и группы Windows в виде части команды **Synchronize** .  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*SkipMembership*|Включает определения безопасности, но исключает сведения о членстве во время выполнения команды **Synchronize** .|  
|*CopyAll*|Включает определения безопасности и сведения о членстве во время выполнения команды **Synchronize** .|  
|*IgnoreSecurity*|Исключает определения безопасности во время выполнения команды **Synchronize** .|  
  
## <a name="see-also"></a>См. также
 [Элемент безопасности &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
