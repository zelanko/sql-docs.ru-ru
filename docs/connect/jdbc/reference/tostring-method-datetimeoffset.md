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
ms.openlocfilehash: ef3cd31068c324475e8edfe8bf8f7c16acc4a2de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968515"
---
# <a name="tostring-method-datetimeoffset"></a>Метод toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает строковое представление объекта **DateTimeOffset** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Строковое представление объекта **DateTimeOffset** .  
  
## <a name="remarks"></a>Remarks  
 Строка имеет формат *гггг*-*мм*-*дд * * чч*:*мм*:*СС*[. *fffffff*] [+ |-]*чч*:*мм*.  
  
 Доли секунды возвращаемой строки дополняются нулями до объявленной точности. Например, значение **DateTimeOffset (6)** со значением "2010-03-10 12:34:56.78-08:00" будет отформатировано с помощью DateTimeOffset. ToString как "2010-03-10 12:34:56.780000-08:00".  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
