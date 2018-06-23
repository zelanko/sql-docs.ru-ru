---
title: Элемент ServerMode | Документы Microsoft
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
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 8448e5ac3111f4c1683ae3dd62dcaef992f3f0e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087216"
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
  
  