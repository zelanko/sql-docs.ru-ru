---
title: Инхериттипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aef8f768dd991e4e6ed740cc56600a6f1a8020e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965954"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Указывает, как объекты наследуют разрешения, заданные с помощью [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Элементы и другие контейнеры, содержащиеся в первичном объекте, наследуют эту запись.|  
|**адинхеритконтаинерс**|2|Другие контейнеры, содержащиеся в первичном объекте, наследуют эту запись.|  
|**адинхеритноне**|0|По умолчанию. Наследование не выполняется.|  
|**адинхеритнопропагате**|4|Флаги **адинхеритобжектс** и **адинхеритконтаинерс** не распространяются на унаследованную запись.|  
|**адинхеритобжектс**|1|Объекты, не являющиеся контейнерами в контейнере, наследуют разрешения.|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
