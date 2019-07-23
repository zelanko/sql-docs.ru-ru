---
title: Метод getDate (int, java.util.Calendar) (SQLServerResultSet) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 150411f7-2a73-4380-b921-9698acd5d1f9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17f2762975f72ccd1e6482ea7120701eacf0c4c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984079"
---
# <a name="getdate-method-int-javautilcalendar-sqlserverresultset"></a>Метод getDate (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Date на языке программирования Java с помощью заданного объекта Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Date getDate(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *Cal*  
  
 Объект Calendar.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Date.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDate определен с помощью метода getDate в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает допустимую часть даты для типа данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] datetime или smalldatetime, а часть времени имеет начальное значение времени Java — 00:00 (полночь) в часовом поясе указанного календаря.  
  
## <a name="see-also"></a>См. также:  
 [Метод getDate (SQLServerResultSet)](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
