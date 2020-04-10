---
title: Метод relative (SQLServerResultSet) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f9233d6e4224e33d9d9c71b1352a792ba19cff2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80904074"
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
 Этот метод relative задается с помощью метода relative в интерфейсе java.sql.ResultSet.  
  
 Если попытаться переместить курсор до первой позиции в результирующем наборе и после последней позиции, то курсор будет располагаться перед первой строкой или после последней строки соответственно. Вызов `relative(0)` допускается, однако не изменяет положение курсора.  
  
 Вызов метода `relative(1)` эквивалентен вызову метода [next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md). Вызов метода `relative(-1)` эквивалентен вызову метода [previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
