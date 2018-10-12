---
title: Метод Relative (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04f353734f6053808972c5cb977658e512222ddb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637132"
---
# <a name="relative-method-sqlserverresultset"></a>Метод relative (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор на заданное количество строк относительно текущей строки в положительном или отрицательном направлении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>Параметры  
 *nRows*  
  
 Значение **int**, которое указывает число строк для перемещения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если курсор находится в строке. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод relative указывается относительный методом в интерфейсе java.sql.ResultSet.  
  
 Если попытаться переместить курсор до первой позиции в результирующем наборе и после последней позиции, то курсор будет располагаться перед первой строкой или после последней строки соответственно. Вызов `relative(0)` допускается, однако не изменяет положение курсора.  
  
 Вызов метода `relative(1)` эквивалентен вызову метода [next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md). Вызов метода `relative(-1)` эквивалентен вызову метода [previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
