---
title: Метод toString (DateTimeOffset) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a37f0e72152ae98a6fda2d49c31f24703cb218d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 Строка имеет формат *гггг*-*мм*-*дд ** hh*:*мм*:*ss*[. *FFFFFFF*] [+ |-]*hh*:*мм*.  
  
 Доли секунды возвращаемой строки дополняются нулями до объявленной точности. Например **datetimeoffset(6)** со значением «12:34:56.78 2010-03-10-08:00» будет отформатировано методом DateTimeOffset.toString как «12:34:56.780000 2010-03-10-08:00 ".  
  
## <a name="see-also"></a>См. также  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
