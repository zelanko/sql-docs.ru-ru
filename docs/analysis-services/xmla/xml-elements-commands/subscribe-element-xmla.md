---
title: Элемент (XMLA) Subscribe | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f784cbe3c33eb6b2587b7b535668e793fac3b138
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574406"
---
# <a name="subscribe-element-xmla"></a>Элемент Subscribe (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Подписывается на трассировку и возвращает набор строк, содержащий события трассировки из экземпляра служб Analysis Services.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
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
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 **Subscribe** команда подписывается на трассировку и возвращает набор строк из указанной трассировки на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Если в элементе **Object** указать объект, отличный от трассировки, возникает ошибка.  
  
 Если **объекта** элемент не указан, трассировка сеанса определяется и выполняется подписка на [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра. Трассировка сеанса возвращает фиксированный набор событий трассировки из текущего сеанса.  
  
 Возвращенный этой командой поток строк завершается, если клиентское приложение закрывает соединение [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра, или если сеанс, в котором **Subscribe** выполняется команда завершается.  
  
## <a name="see-also"></a>См. также
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
