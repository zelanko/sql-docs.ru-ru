---
title: Метод Relative (SQLServerResultSet) | Документы Microsoft
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
ms.topic: article
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d210c40ac0c288ef57e74f37218515e21148fdb3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="relative-method-sqlserverresultset"></a>Метод Relative (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор на заданное количество строк относительно текущей строки в положительном или отрицательном направлении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>Параметры  
 *nRows*  
  
 **Int** , указывающее количество строк для перемещения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если курсор находится в строке. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод relative указывается относительный методом в интерфейсе java.sql.ResultSet.  
  
 Если попытаться переместить курсор до первой позиции в результирующем наборе и после последней позиции, то курсор будет располагаться перед первой строкой или после последней строки соответственно. Вызов `relative(0)` является допустимым, но не изменяет положение курсора.  
  
 Вызов метода `relative(1)` совпадает с вызовом метода [Далее](../../../connect/jdbc/reference/next-method-sqlserverresultset.md) метод. Вызов метода `relative(-1)` совпадает с вызовом метода [предыдущих](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
