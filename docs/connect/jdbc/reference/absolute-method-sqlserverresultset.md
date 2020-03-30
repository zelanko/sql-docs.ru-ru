---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66bdbfa417077e70be7969b28ae851a0244e54ca
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67956068"
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
  
  
