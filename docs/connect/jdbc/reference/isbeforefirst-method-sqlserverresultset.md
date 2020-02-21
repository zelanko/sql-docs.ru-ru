---
title: Метод isBeforeFirst (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isBeforeFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e0e2bd28-6949-47dc-b9dd-145ffb337069
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ffe17993b3a03563ec20e8f509e6eae2f6ed47cb
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977789"
---
# <a name="isbeforefirst-method-sqlserverresultset"></a>Метод isBeforeFirst (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает логическое значение, которое показывает, располагается ли курсор перед первой строкой этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isBeforeFirst()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если курсор находится перед первой строкой. Значение **false**, если курсор находится в любой другой позиции либо результирующий набор не содержит строк.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод isBeforeFirst определен с помощью метода isBeforeFirst в интерфейсе java.sql.ResultSet.  
  
 Если этот метод используется с динамическими курсорами, включая однопроходные курсоры только для чтения, а свойство соединения selectMethod имеет значение cursor, то вызывается исключение.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
