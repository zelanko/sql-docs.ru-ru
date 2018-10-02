---
title: Метод valueOf (java.sql.Timestamp, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ced75c886fcc0bf58d1671e50a213d5a6003a97
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704108"
---
# <a name="valueof-method-javasqltimestamp-int"></a>Метод valueOf (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект **DateTimeOffset**, представляющий точку во времени с указанным смещением относительно времени по Гринвичу (GMT). Объекту нужно передать значение java.sql.Timestamp и значение смещения в минутах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, int minutesOffset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *timestamp*  
  
 Значениеjava.sql.Timestamp.  
  
 *minutesOffset*  
  
 Смещение в минутах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект DateTimeOffset, представляющий точку во времени, заданную объектом и java.sql.Timestamp с указанным смещением минутах относительно GMT.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
