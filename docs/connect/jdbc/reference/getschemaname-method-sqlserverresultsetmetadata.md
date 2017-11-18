---
title: "Метод getSchemaName (SQLServerResultSetMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSetMetaData.getSchemaName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2d0063ab-d5d7-420f-b388-36d5169b1358
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 22181dbd0d5132e9c7a86ea0e0db76346d20022f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getschemaname-method-sqlserverresultsetmetadata"></a>Метод getSchemaName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя схемы для таблицы, содержащей указанный столбец.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSchemaName(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *столбец*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее имя схемы.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSchemaName указывается с помощью метода getSchemaName в интерфейсе java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

