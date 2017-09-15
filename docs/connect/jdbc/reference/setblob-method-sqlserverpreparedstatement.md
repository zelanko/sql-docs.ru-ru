---
title: "Метод (SQLServerPreparedStatement) setBlob | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerPreparedStatement.setBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 218ff486-3f31-49e4-ad81-a423246a8307
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d05945d59b05c43970b8e58104aaf6b2c3cd2b85
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setblob-method-sqlserverpreparedstatement"></a>setBlob метод (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру для заданного объекта BLOB-объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setBlob(int i,  
                          java.sql.Blob x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *я*  
  
 **Int** указывает номер параметра.  
  
 *x*  
  
 Большой двоичный объект.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setBlob указывается с помощью метода setBlob в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
