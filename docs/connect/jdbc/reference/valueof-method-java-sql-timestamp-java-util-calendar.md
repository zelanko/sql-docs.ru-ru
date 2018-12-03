---
title: Метод valueOf (java.sql.Timestamp, java.util.Calendar) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea08f3b58894ff269972dc2348d71fb2d589959c
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52398204"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Метод valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект **DateTimeOffset**, представляющий точку во времени с указанным смещением относительно времени по Гринвичу (GMT). Объекту нужно передать значение java.util.Timestamp и значение смещения java.util.Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Параметры  
 *timestamp*  
  
 Значениеjava.sql.Timestamp.  
  
 *calendar*  
  
 Значение смещения.  Компоненты даты и времени *календаря* устанавливается в соответствии с *timestamp* значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект DateTimeOffset, представляющий точку во времени, заданную объектом java.sql.Timestamp объект в объект заданного java.util.Calendar часового пояса.  
  
## <a name="remarks"></a>Remarks  
 Этот метод также задает объект java.util.Calendar до точки во времени, заданную объектом java.sql.Timestamp.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
