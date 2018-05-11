---
title: Элемент AccountType (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e07561d0cd4272c202786f931fdd0dbc3c4eda8d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
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
  
  
