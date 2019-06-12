---
title: Метод toString (DateTimeOffset) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 64186b6add766a21e0881fb6b3f59d49048334e8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778592"
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
  
## <a name="remarks"></a>Remarks  
 Строка имеет формат *гггг*-*мм*-*дд ** hh*:*мм*:*ss*[. *FFFFFFF*] [+ |-]*hh*:*мм*.  
  
 Доли секунды возвращаемой строки дополняются нулями до объявленной точности. Например **datetimeoffset(6)** со значением «12:34:56.78 2010-03-10-08:00» будет отформатировано методом DateTimeOffset.toString как «12:34:56.780000 2010-03-10-08:00 ".  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
