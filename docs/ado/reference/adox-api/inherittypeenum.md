---
title: InheritTypeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4d822bd48d399b767c6676e014abe3d733aa5bc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Указывает, каким образом объекты будут наследовать разрешения, установленные с [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Объекты и другие контейнеры, содержащихся в объекте основной наследуют запись.|  
|**adInheritContainers**|2|Запись наследуют других контейнеров, содержащихся в основной объект.|  
|**adInheritNone**|0|По умолчанию. Наследование не происходит.|  
|**adInheritNoPropagate**|4|**AdInheritObjects** и **adInheritContainers** флаги не распространяются на наследуемые запись.|  
|**adInheritObjects**|1|Не являющиеся контейнерами объекты в контейнере наследуют разрешения.|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
