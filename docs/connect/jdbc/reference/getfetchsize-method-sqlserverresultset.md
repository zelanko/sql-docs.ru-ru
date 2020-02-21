---
title: Метод getFetchSize (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7bc96930-b0c9-42f6-8df9-1d8d824408b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 874d4032fc3306b180d0fafefc7a4ac085b5af29
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983230"
---
# <a name="getfetchsize-method-sqlserverresultset"></a>Метод getFetchSize (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение размера выборки для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getFetchSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое указывает текущий размер выборки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFetchSize задается с помощью метода getFetchSize в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
