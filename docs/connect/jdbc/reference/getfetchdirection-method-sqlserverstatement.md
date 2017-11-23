---
title: "Метод getFetchDirection (SQLServerStatement) | Документы Microsoft"
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
apiname: SQLServerStatement.getFetchDirection
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff5ec8aa9e65c3c2881bef50f25dd8be726d8908
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>Метод getFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает направление для выборки строк из таблиц базы данных, значение по умолчанию для результирующих наборов, которые создаются из этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.  
  
> [!NOTE]  
>  Этот метод не реализован в настоящее время [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Поэтому он всегда будет возвращать FETCH_UNKNOWN.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее направление выборки, который задается параметром [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md) метод.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getFetchDirection указывается с помощью метода getFetchDirection в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
