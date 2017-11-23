---
title: "Метод setFetchSize (SQLServerStatement) | Документы Microsoft"
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
apiname: SQLServerStatement.setFetchSize
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69aaab5db90e9affaa46f1bb9aff80265f9759e4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setfetchsize-method-sqlserverstatement"></a>Метод setFetchSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Предоставляет [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] подсказку относительно числа строк, которые должны быть извлечены из базы данных, при необходимости в дополнительных строках.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Параметры  
 *строки*  
  
 **Int** , указывающее количество строк для выборки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setFetchSize указывается с помощью метода setFetchSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
