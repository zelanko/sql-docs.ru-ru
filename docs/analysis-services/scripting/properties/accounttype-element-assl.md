---
title: Элемент AccountType (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AccountType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5225a1f9ee45754c60c46f8cc9c3fea3d2af0ec1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="accounttype-element-assl"></a>Элемент AccountType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит имя типа учетной записи, определенные в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Учетная запись](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Remarks  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Доход*|Счет является счетом доходов.|  
|*О расходах*|Счет является счетом расходов.|  
|*Поток*|Счет является кассовым счетом.|  
|*Баланс*|Счет является балансовым счетом.|  
|*Активов*|Счет является счетом актива.|  
|*Ответственности*|Счет является счетом обязательств.|  
|*Статистические*|Счет является статистическим счетом.|  
  
 Перечисление, соответствующее разрешенным значениям для **AccountType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Accounts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
