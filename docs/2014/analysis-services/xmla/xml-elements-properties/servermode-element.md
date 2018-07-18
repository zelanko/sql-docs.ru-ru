---
title: Элемент ServerMode | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f8cb39-dad7-433b-b7b7-fb1625f76a84
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b329f9882b9eff2adf1a79041ea83c51a627f15
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37239454"
---
# <a name="servermode-element"></a>Элемент ServerMode
  Серверный элемент `ServerMode` указывает режим работы сервера.  
  
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
|Родительские элементы|[Server](../../scripting/objects/server-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Сервер работает в одном из следующих режимов.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Многомерные*|Режим многомерных выражений и интеллектуального анализа данных.|  
|*Табличные*|Табличный режим|  
|*SharePoint*|Режим интеграции с SharePoint|  
  
## <a name="see-also"></a>См. также  
 [Server](../../scripting/objects/server-element-assl.md)  
  
  
