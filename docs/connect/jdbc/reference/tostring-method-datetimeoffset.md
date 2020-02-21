---
title: Метод toString (DateTimeOffset) | Документация Майкрософт
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
ms.openlocfilehash: f3acffe6a922084fd63e38a8e212b5cf86d6b278
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "71096907"
---
# <a name="tostring-method-datetimeoffset"></a>Метод toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает строковое представление текущего объекта **DateTimeOffset**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Строковое представление текущего объекта **DateTimeOffset**.  
  
## <a name="remarks"></a>Remarks  
 Эта строка имеет формат `YYYY-MM-DD HH:mm:ss[.fffffff] [+|-]HH:mm`.  
  
 Доли секунды возвращаемой строки дополняются нулями до объявленной точности. Например, **DateTimeOffset (6)** со значением "2010-03-10 12:34:56.78 -08:00" при выполнении DateTimeOffset.toStringбудет отформатировано как "2010-03-10 12:34:56.780000 -08:00".  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
