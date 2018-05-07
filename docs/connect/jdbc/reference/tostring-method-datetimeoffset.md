---
title: Метод toString (DateTimeOffset) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c9290b3a86d97efb3dd507819d4e858f3bf1ba7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
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
  
  
