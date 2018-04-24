---
title: InheritTypeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
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
ms.workload: Inactive
ms.openlocfilehash: e4be349722f849c0a5f059236b4a1d689cf18494
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
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
