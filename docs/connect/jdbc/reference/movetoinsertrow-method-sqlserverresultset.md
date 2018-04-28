---
title: Метод (SQLServerResultSet) moveToInsertRow | Документы Microsoft
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
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f39608188e9de998c5f431561cf1482f5d50b3f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор в строку вставки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод moveToInsertRow указывается с помощью метода moveToInsertRow в интерфейсе java.sql.ResultSet.  
  
 Текущая позиция курсора запоминается, пока курсор располагается в строке вставки. Строка вставки — это специальная строка, связанная с обновляемым результирующим набором. Фактически она служит буфером, в котором можно создать новую строку, вызывая методы обновления, перед добавлением строки в результирующий набор.  
  
 Только обновления, считывания и [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) методы могут вызываться, когда курсор находится в строке вставки. Все столбцы в результирующем наборе должны быть, данное значение при каждом вызове этого метода и перед вызовом insertRow. Метод обновления должен вызываться перед вызовом метода считывания для значения столбца.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
