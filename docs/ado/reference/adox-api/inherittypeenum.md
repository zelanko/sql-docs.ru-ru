---
title: InheritTypeEnum | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: b17bdd7204ec52ef5a2fc27d7bc364be7f017189
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66706494"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Указывает, как объекты наследуют разрешения, установленные с [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Объекты и другие контейнеры, содержащихся в объекте основной наследуют запись.|  
|**adInheritContainers**|2|Другие контейнеры, которые содержатся в объекте основной наследуют запись.|  
|**adInheritNone**|0|По умолчанию. Происходит, не поддерживают наследование.|  
|**adInheritNoPropagate**|4|**AdInheritObjects** и **adInheritContainers** флаги не распространяются на унаследованные записи.|  
|**adInheritObjects**|1|Non контейнер объектов в контейнере, наследуют разрешения.|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
