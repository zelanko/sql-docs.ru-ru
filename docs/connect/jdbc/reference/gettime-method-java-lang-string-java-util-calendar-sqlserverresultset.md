---
description: Метод getTime (java.lang.String, java.util.Calendar) (SQLServerResultSet)
title: Метод getTime (java.lang.String, java.util.Calendar) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 13b51f77-cec9-45fc-862e-3d2bb2d718d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2e1897aa9db223e118863c563f8d81c8b7f985c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434266"
---
# <a name="gettime-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Метод getTime (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Time на языке программирования Java с помощью указанного объекта Calendar.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *colName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
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
  
  
