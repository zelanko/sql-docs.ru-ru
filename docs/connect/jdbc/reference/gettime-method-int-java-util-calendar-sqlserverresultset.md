---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 82f4c082145fc9d043047390d0b07380f37c798b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979138"
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
  
  
