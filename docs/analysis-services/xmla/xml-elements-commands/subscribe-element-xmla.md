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
ms.openlocfilehash: 548336f5e891cc41c485bed4047c1223d0f9344c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="subscribe-element-xmla"></a>Элемент Subscribe (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Подписывается на трассировку и возвращает набор строк, содержащий события трассировки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
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
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
