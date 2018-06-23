---
title: Элемент AccountType (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AccountType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff7203d2882689b21a6ab3171880c26a8d385f7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190078"
---
# <a name="accounttype-element-assl"></a>Элемент AccountType (ASSL)
  Содержит имя типа учетной записи, определенные в [базы данных](../objects/database-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Учетная запись](../objects/account-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Доход*|Счет является счетом доходов.|  
|*О расходах*|Счет является счетом расходов.|  
|*Поток*|Счет является кассовым счетом.|  
|*Баланс*|Счет является балансовым счетом.|  
|*Активов*|Счет является счетом актива.|  
|*Ответственности*|Счет является счетом обязательств.|  
|*Статистические*|Счет является статистическим счетом.|  
  
 Перечисление, соответствующее допустимым значениям элемента `AccountType` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>См. также  
 [Учетные записи элемента &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  