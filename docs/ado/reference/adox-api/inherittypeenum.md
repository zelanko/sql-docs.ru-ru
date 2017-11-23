---
title: "InheritTypeEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: InheritTypeEnum
helpviewer_keywords: InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9269c58d9f5c172a6c640668382b00fd66c5dda0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Указывает, каким образом объекты будут наследовать разрешения, установленные с [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Объекты и другие контейнеры, содержащихся в объекте основной наследуют запись.|  
|**adInheritContainers**|2|Запись наследуют других контейнеров, содержащихся в основной объект.|  
|**adInheritNone**|0|По умолчанию. Наследование не происходит.|  
|**adInheritNoPropagate**|4|**AdInheritObjects** и **adInheritContainers** флаги не распространяются на наследуемые запись.|  
|**adInheritObjects**|1|Не являющиеся контейнерами объекты в контейнере наследуют разрешения.|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
