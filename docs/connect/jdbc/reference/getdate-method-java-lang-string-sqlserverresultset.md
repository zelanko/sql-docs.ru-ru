---
title: Метод getDate (java.lang.String) для значения имени столбца | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 821058ae-cbe3-4a14-aa02-d55e45491437
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c534c043de11d9123beaaa36f38c4bbd009012c9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67983910"
---
# <a name="getdate-method-javalangstring-sqlserverresultset"></a>Метод getDate (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Date на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Date getDate(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Date.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDate определен с помощью метода getDate в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает допустимую часть даты для типа данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] datetime или smalldatetime, а часть времени имеет начальное значение времени Java — 00:00 (полночь).  
  
## <a name="see-also"></a>См. также:  
 [Метод getDate (SQLServerResultSet)](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
