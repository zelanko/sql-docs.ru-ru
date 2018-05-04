---
title: Метод getArray (java.lang.String) (SQLServerResultSet) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getArray java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a98d159b-1fae-482a-9465-5411ce60f901
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5e6a92ae7c1c80ae3558ab64906504e08e66158
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getarray-method-javalangstring-sqlserverresultset"></a>Метод getArray (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как объект массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Array getArray(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColName*  
  
 Объект **строка** , содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект массива.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getArray указывается с помощью getArray метода в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также  
 [Метод getArray &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
