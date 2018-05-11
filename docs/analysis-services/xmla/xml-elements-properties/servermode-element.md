---
title: Элемент ServerMode | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 362e91994f4c195a6fe2d48a798444041d6855e8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="servermode-element"></a>Элемент ServerMode
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Серверный элемент **ServerMode** указывает режим работы сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Server>  
...  
   <ddl300:ServerMode>...</ddl300:ServerMode>  
...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|(нет)|  
|Количество элементов|0—1: Необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Сервер работает в одном из следующих режимов.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Многомерные*|Режим многомерных выражений и интеллектуального анализа данных.|  
|*Табличные*|Табличный режим|  
|*SharePoint*|Режим интеграции с SharePoint|  
  
## <a name="see-also"></a>См. также  
 [Server](../../../analysis-services/scripting/objects/server-element-assl.md)  
  
  
