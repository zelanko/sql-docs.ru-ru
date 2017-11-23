---
title: "Метод (SQLServerResultSet) cancelRowUpdates | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.cancelRowUpdates
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 2ecacca4-f7bc-4f5d-886a-da7747fdccae
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6121f6f3b7608602ec64785df979b70d53c5bf53
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="cancelrowupdates-method-sqlserverresultset"></a>cancelRowUpdates метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Отменяет обновления текущей строки в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void cancelRowUpdates()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод cancelRowUpdates указывается с помощью метода cancelRowUpdates в интерфейсе java.sql.ResultSet.  
  
 Этот метод может вызываться после вызова метода обновления и перед вызовом метода [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) метод для отката обновлений, которые были внесены в строку. Если не были обновлены или уже был вызван updateRow, этот метод не оказывает влияния.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
