---
title: "Метод createStatement (int, int) | Документы Microsoft"
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
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a9229e66b071f4fd33077c4e3c7c780f9a1059aa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="createstatement-method-int-int"></a>Метод createStatement (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект, который формирует [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты с заданным типом и видом параллелизма.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Параметры  
 *resultSetType*  
  
 **Int** значение, представляющее тип результирующего набора.  
  
 *resultSetConcurrency*  
  
 **Int** значение, представляющее тип параллелизма результирующего набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект инструкции.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод createStatement указывается с помощью метода createStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод createStatement &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

