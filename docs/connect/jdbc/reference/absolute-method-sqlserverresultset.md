---
description: Метод absolute (SQLServerResultSet)
title: Метод absolute (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 260849163934c32cf1d671af024856f81cad7db3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438316"
---
# <a name="absolute-method-sqlserverresultset"></a>Метод absolute (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор в заданную строку этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>Параметры  
 *row*  
  
 Значение **int**, которое указывает номер строки для перехода. Может быть положительным, отрицательным или равняться 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если курсор перемещен в указанную позицию. **false**, если курсор находится перед первой строкой или после последней строки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод absolute определен с помощью метода absolute в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
