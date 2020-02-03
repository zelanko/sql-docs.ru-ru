---
title: Метод getArray (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getArray java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a98d159b-1fae-482a-9465-5411ce60f901
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05d5fb6bd412e55290ab893cf3552db6c6bcc34f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954343"
---
# <a name="getarray-method-javalangstring-sqlserverresultset"></a>Метод getArray (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение заданного имени столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Array.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Array getArray(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *colName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Array.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getArray определен с помощью метода getArray в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getArray (SQLServerResultSet)](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
