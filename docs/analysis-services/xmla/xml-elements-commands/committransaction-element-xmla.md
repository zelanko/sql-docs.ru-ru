---
title: Элемент CommitTransaction (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9afae9806592f09ebc32611d4566d7c67e65d743
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="committransaction-element-xmla"></a>Элемент CommitTransaction (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Фиксирует транзакцию в текущем сеансе с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <CommitTransaction />  
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
 Команда **CommitTransaction** фиксирует активную транзакцию, явно определенную с использованием элемента **BeginTransaction** в текущем сеансе. Если еще не существует активной транзакции, возникает ошибка. Если активная транзакция уже существует, то в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] уменьшается количество ссылок на транзакции для текущего сеанса. Если количество ссылок на явно определенные активные транзакции достигает нуля, в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] фиксируется соответствующая транзакция.  
  
## <a name="see-also"></a>См. также  
 [Элемент BeginTransaction &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)   
 [Элемент Cancel &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Элемент RollbackTransaction &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
