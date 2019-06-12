---
title: Метод getBigDecimal (int, int) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBigDecimal (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c99d0772-b26c-492c-a643-2813b5429993
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e017453713347ff3c3dc5696fb0a4c63315413aa
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799916"
---
# <a name="getbigdecimal-method-int-int-sqlserverresultset"></a>Метод getBigDecimal (int, int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение индекса указанного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) по заданному масштабу.  
  
> [!NOTE]  
>  Этот метод является устаревшим в спецификации JDBC. Вместо этого следует использовать метод [getBigDecimal (int)](../../../connect/jdbc/reference/getbigdecimal-method-int-sqlserverresultset.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.math.BigDecimal getBigDecimal(int columnIndex,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *масштаб*  
  
 Значение типа **int**, указывающее количество разрядов справа от десятичного разделителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект BigDecimal.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getBigDecimal указывается с помощью метода getBigDecimal в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBigDecimal (SQLServerResultSet)](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
