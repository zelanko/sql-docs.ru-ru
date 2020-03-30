---
title: Метод getSQLXML (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9c7b10-026f-4a51-8d60-e6871d1abd02
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ecf5030c4722f2e5681cb199993a48fea0e22462
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979680"
---
# <a name="getsqlxml-method-javalangstring-sqlserverresultset"></a>Метод getSQLXML (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта SQLXML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение **String**, которое указывает метку столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLXML.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSQLXML определен с помощью метода getSQLXML в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getSQLXML (SQLServerResultSet)](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
