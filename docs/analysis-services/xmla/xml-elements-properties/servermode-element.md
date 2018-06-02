---
title: Элемент ServerMode | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21e9344ef945311b3af07398e6e927482718f5ff
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576266"
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
  
  
