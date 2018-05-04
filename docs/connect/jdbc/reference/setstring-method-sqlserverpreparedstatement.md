---
title: Метод (SQLServerPreparedStatement) setString | Документы Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 25dabdc9-c60f-485a-87eb-306067964765
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11d477d5dce0b2ff6c12d645c83228fe8fe4bef4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setstring-method-sqlserverpreparedstatement"></a>setString метод (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный параметр заданного **строка** значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setString(int index,  
                            java.lang.String str)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 **Int** указывает номер параметра.  
  
 *STR*  
  
 Объект **строка** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setString задается с помощью метода setString в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
