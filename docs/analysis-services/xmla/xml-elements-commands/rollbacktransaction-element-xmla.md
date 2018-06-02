---
title: Элемент RollbackTransaction (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d1bf63b2e3db0add86927c2f624a01fafa31e3d7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574506"
---
# <a name="rollbacktransaction-element-xmla"></a>Элемент RollbackTransaction (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Откат транзакции в текущем сеансе с экземпляром служб Analysis Services.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <RollbackTransaction />  
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
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Команда **RollbackTransaction** выполняет откат в текущем сеансе всех активных транзакций, явно определенных с помощью элемента **BeginTransaction** . Если еще не существует активной транзакции, возникает ошибка. Если какая-либо активная транзакция уже существует, в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] уменьшается количество ссылок на транзакции для текущего сеанса до нуля, что приводит к откату всех активных транзакций.  
  
## <a name="see-also"></a>См. также
 [Элемент BeginTransaction &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Элемент Cancel &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Элемент CommitTransaction &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
