---
title: "Метод getSQLXML (int) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1b32d3a-d7c9-4086-ae2b-fc1da96949b1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1709ee44e59c4f2b315a1f9eb7f6d1e042474f89
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getsqlxml-method-int"></a>Метод getSQLXML (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта SQLXML, заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.SQLXML getSQLXML(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSQLXML задается методом getSQLXML в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getSQLXML &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

