---
title: "Элемент BeginTransaction (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
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
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 677ad07e9ce6206bbc4e7946ec111f8865bcfcce
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="begintransaction-element-xmla"></a>Элемент BeginTransaction (XML для аналитики)
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
  
## <a name="remarks"></a>Замечания  
 Команда **BeginTransaction** запускает активную транзакцию в текущем сеансе. Если активная транзакция уже существует, экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] увеличивает значение счетчика ссылок на транзакции для текущего сеанса. В противном случае экземпляр запускает новую транзакцию и устанавливает значение счетчика ссылок для текущего сеанса в 1. Если активная транзакция задана явно командой **BeginTransaction** , все последующие команды выполняются в явно заданной транзакции.  
  
 Если текущий сеанс завершается, а значение счетчика ссылок для транзакций больше нуля, выполняется откат всех активных транзакций.  
  
 Если в текущем сеансе отсутствуют явно заданные активные транзакции, каждая команда выполняется в неявно определенной транзакции. Неявно определенная транзакция фиксируется при успешном завершении команды, в противном случае выполняется ее откат.  
  
## <a name="see-also"></a>См. также:  
 [Отменить элемент &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Элемент CommitTransaction &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Элемент RollbackTransaction &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Команды &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
