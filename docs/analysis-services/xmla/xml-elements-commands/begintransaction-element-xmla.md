---
title: Элемент BeginTransaction (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 452bf0463a073ec4033b9a0c62231838b8a7978a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="begintransaction-element-xmla"></a>Элемент BeginTransaction (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Начинает транзакцию в текущем сеансе с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <BeginTransaction />  
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
 Команда **BeginTransaction** запускает активную транзакцию в текущем сеансе. Если активная транзакция уже существует, экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] увеличивает значение счетчика ссылок на транзакции для текущего сеанса. В противном случае экземпляр запускает новую транзакцию и устанавливает значение счетчика ссылок для текущего сеанса в 1. Если активная транзакция задана явно командой **BeginTransaction** , все последующие команды выполняются в явно заданной транзакции.  
  
 Если текущий сеанс завершается, а значение счетчика ссылок для транзакций больше нуля, выполняется откат всех активных транзакций.  
  
 Если в текущем сеансе отсутствуют явно заданные активные транзакции, каждая команда выполняется в неявно определенной транзакции. Неявно определенная транзакция фиксируется при успешном завершении команды, в противном случае выполняется ее откат.  
  
## <a name="see-also"></a>См. также  
 [Элемент Cancel &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Элемент CommitTransaction &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Элемент RollbackTransaction &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Команды & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
