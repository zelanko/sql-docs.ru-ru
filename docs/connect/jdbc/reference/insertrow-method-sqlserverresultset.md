---
title: Метод insertRow (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 611ba86c25f78cda15fcac53d8f31311d88e4840
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696875"
---
# <a name="insertrow-method-sqlserverresultset"></a>Метод insertRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Добавляет содержимое строки вставки в этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) и в базу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод insertRow указывается с помощью метода insertRow в интерфейсе java.sql.ResultSet.  
  
 В момент вызова этого метода курсор должен располагаться в строке вставки. После вызова этого метода курсор остается в строке вставки, а результирующий набор остается в режиме вставки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
