---
title: "Метод setNull (int, int, java.lang.String) | Документы Microsoft"
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
- SQLServerPreparedStatement.setNull (int, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43c74e06-2858-49ba-bae7-b88808e5fff4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f52604e2e94c1599ebbe9453789e502aea9e17f5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setnull-method-int-int-javalangstring"></a>Метод setNull (int, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный параметр в значение NULL по заданному имени и типу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNull(int paramIndex,  
                          int sqlType,  
                          java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *paramIndex*  
  
 **Int** указывает номер параметра.  
  
 *sqlType*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
 *Имя типа*  
  
 Объект **строка** указывает полное имя параметра, которое должно быть задано.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setNull указывается с помощью setNull метода в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNull &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

