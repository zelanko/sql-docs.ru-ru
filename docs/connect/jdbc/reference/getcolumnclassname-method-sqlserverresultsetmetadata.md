---
title: Метод getColumnClassName (SQLServerResultSetMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnClassName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2c118790-5dd2-4b10-93b6-7f065ee324ce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37c791c80c679afd70f4f1d2f3f2770fb0f38a16
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67952999"
---
# <a name="getcolumnclassname-method-sqlserverresultsetmetadata"></a>Метод getColumnClassName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает полное имя Java-класса, экземпляры которого создаются при вызове метода [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) класса [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) для получения значения столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getColumnClassName(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *column*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее полное имя класса.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getColumnClassName указывается с помощью метода getColumnClassName в интерфейсе java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
