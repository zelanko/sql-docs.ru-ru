---
title: Элемент BeginTransaction (XML для Аналитики) | Документация Майкрософт
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
- BeginTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1685c1c61c248cf37672cab17ccf3144e7d5e7ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253046"
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
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Команда `BeginTransaction` запускает активную транзакцию в текущем сеансе. Если активная транзакция уже существует, экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] увеличивает значение счетчика ссылок на транзакции для текущего сеанса. В противном случае экземпляр запускает новую транзакцию и устанавливает значение счетчика ссылок для текущего сеанса в 1. Если активная транзакция задана явно командой `BeginTransaction`, все последующие команды выполняются в явно заданной транзакции.  
  
 Если текущий сеанс завершается, а значение счетчика ссылок для транзакций больше нуля, выполняется откат всех активных транзакций.  
  
 Если в текущем сеансе отсутствуют явно заданные активные транзакции, каждая команда выполняется в неявно определенной транзакции. Неявно определенная транзакция фиксируется при успешном завершении команды, в противном случае выполняется ее откат.  
  
## <a name="see-also"></a>См. также  
 [Элемент Cancel &#40;XML для Аналитики&#41;](cancel-element-xmla.md)   
 [Элемент CommitTransaction &#40;XML для Аналитики&#41;](committransaction-element-xmla.md)   
 [Элемент RollbackTransaction &#40;XML для Аналитики&#41;](rollbacktransaction-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
