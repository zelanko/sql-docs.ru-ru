---
title: InheritTypeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
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
ms.openlocfilehash: b3a167913b23005cf2b78e4acc682ec2af75157c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286653"
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
