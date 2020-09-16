---
description: Метод getTime (int, java.util.Calendar) (SQLServerResultSet)
title: Метод getTime (int, java.util.Calendar) (SQLServerResultSet) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTime (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d21e0c1d-9d6e-468f-8b11-cc7209b2c2e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b647e4dff3980e5828a92d54866f17ddf8790d97
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434246"
---
# <a name="gettime-method-int-javautilcalendar-sqlserverresultset"></a>Метод getTime (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Time на языке программирования Java с помощью заданного объекта Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *cal*  
  
 Объект Calendar.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Time.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTime определен с помощью метода getTime в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает допустимую часть времени для типа данных datetime или smalldatetime [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а часть даты имеет начальное значение даты Java — 1 января 1970 г. в часовом поясе указанного календаря.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTime (SQLServerResultSet)](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
