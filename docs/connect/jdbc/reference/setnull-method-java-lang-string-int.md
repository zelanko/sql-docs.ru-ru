---
title: "Метод setNull (java.lang.String, int) | Документы Microsoft"
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
- SQLServerCallableStatement.setNull (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d7e267-d9de-407a-b1a9-abdc2623478d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a19833c4f69ca90f084ce76579d1357263b25eb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setnull-method-javalangstring-int"></a>Метод setNull (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает значение NULL для параметра, определяемого по заданному типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setNull(java.lang.String sCol,  
                    int nType)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *nType*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setNull указывается с помощью setNull метода в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNull &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
