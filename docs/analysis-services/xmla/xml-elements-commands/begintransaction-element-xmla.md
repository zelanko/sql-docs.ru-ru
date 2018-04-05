---
title: Элемент BeginTransaction (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BeginTransaction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e7ce11d146e54e2ee90c7944bc0ee27eb4f01175
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="begintransaction-element-xmla"></a>Элемент BeginTransaction (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Начинает транзакцию в текущем сеансе с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <BeginTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Команда **BeginTransaction** запускает активную транзакцию в текущем сеансе. Если активная транзакция уже существует, экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] увеличивает значение счетчика ссылок на транзакции для текущего сеанса. В противном случае экземпляр запускает новую транзакцию и устанавливает значение счетчика ссылок для текущего сеанса в 1. Если активная транзакция задана явно командой **BeginTransaction** , все последующие команды выполняются в явно заданной транзакции.  
  
 Если текущий сеанс завершается, а значение счетчика ссылок для транзакций больше нуля, выполняется откат всех активных транзакций.  
  
 Если в текущем сеансе отсутствуют явно заданные активные транзакции, каждая команда выполняется в неявно определенной транзакции. Неявно определенная транзакция фиксируется при успешном завершении команды, в противном случае выполняется ее откат.  
  
## <a name="see-also"></a>См. также:  
 [Отменить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Элемент CommitTransaction &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Элемент RollbackTransaction &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
