---
title: "Метод toString (DateTimeOffset) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4b0c31538c7260b81a88822099f56a05b70a0a96
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="tostring-method-datetimeoffset"></a>Метод toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает строковое представление **DateTimeOffset** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Строковое представление **DateTimeOffset** объекта.  
  
## <a name="remarks"></a>Замечания  
 Строка имеет формат *гггг*-*мм*-*дд**hh*:*мм*: *ss*[. *FFFFFFF*] [+ |-]*hh*:*мм*.  
  
 Доли секунды возвращаемой строки дополняются нулями до объявленной точности. Например **datetimeoffset(6)** со значением «12:34:56.78 2010-03-10-08:00» будет отформатировано методом DateTimeOffset.toString как «12:34:56.780000 2010-03-10-08:00 ".  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  

