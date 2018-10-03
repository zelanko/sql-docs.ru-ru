---
title: Элемент RollbackTransaction (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RollbackTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RollbackTransaction
- microsoft.xml.analysis.rollbacktransaction
- urn:schemas-microsoft-com:xml-analysis#RollbackTransaction
helpviewer_keywords:
- RollbackTransaction command
ms.assetid: 40e7dc00-656f-412f-97f0-d05bf7caa196
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ae78f589c1c85713c751a737d6fb93fac9efeda
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218824"
---
# <a name="rollbacktransaction-element-xmla"></a>Элемент RollbackTransaction (XML для аналитики)
  Выполняет откат транзакции в текущем сеансе с экземпляром [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
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
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Команда `RollbackTransaction` выполняет откат в текущем сеансе всех активных транзакций, явно определенных с помощью элемента `BeginTransaction`. Если еще не существует активной транзакции, возникает ошибка. Если какая-либо активная транзакция уже существует, в экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] уменьшается количество ссылок на транзакции для текущего сеанса до нуля, что приводит к откату всех активных транзакций.  
  
## <a name="see-also"></a>См. также  
 [Элемент BeginTransaction &#40;XML для Аналитики&#41;](begintransaction-element-xmla.md)   
 [Элемент Cancel &#40;XML для Аналитики&#41;](cancel-element-xmla.md)   
 [Элемент CommitTransaction &#40;XML для Аналитики&#41;](committransaction-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
