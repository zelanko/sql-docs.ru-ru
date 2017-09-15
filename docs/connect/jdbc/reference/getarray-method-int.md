---
title: "Метод getArray (int) | Документы Microsoft"
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
- SQLServerCallableStatement.getArray (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5b839d3f-5a4e-43da-b93c-dc9e0f6d4b3b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c507bec7b1bc5d3821ece0a21df865c7bae2a8d1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getarray-method-int"></a>Метод getArray (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде массива объектом по заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Array getArray(int i)  
```  
  
#### <a name="parameters"></a>Параметры  
 *я*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект массива.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getArray указывается с помощью getArray метода в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getArray &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
