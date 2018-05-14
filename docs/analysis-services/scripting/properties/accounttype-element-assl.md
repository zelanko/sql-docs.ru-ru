---
title: Элемент AccountType (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5258ff60c8dfafefbf81f87d3538c396c085ccac
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="accounttype-element-assl"></a>Элемент AccountType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Содержит имя типа учетной записи, определенные в [базы данных](../../../analysis-services/scripting/objects/database-element-assl.md) элемента.  
  
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
|Родительские элементы|[Учетная запись](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Доходы*|Счет является счетом доходов.|  
|*Расход*|Счет является счетом расходов.|  
|*Поток*|Счет является кассовым счетом.|  
|*Баланс*|Счет является балансовым счетом.|  
|*Актив*|Счет является счетом актива.|  
|*Обязательство*|Счет является счетом обязательств.|  
|*Статистические*|Счет является статистическим счетом.|  
  
 Перечисление, соответствующее разрешенным значениям для **AccountType** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>См. также  
 [Учетные записи элемента &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
