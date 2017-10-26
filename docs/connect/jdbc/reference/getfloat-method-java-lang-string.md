---
title: "Метод getFloat (java.lang.String) | Документы Microsoft"
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
- SQLServerCallableStatement.getFloat (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6492341-fdc2-449c-9d03-95a5dadf1bb0
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f10c51b95abd620d1ee129793809ccbe7f299c25
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getfloat-method-javalangstring"></a>Метод getFloat (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде **float** на Java по заданному имени параметра языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public float getFloat(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **float** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getFloat указывается с помощью метода getFloat в интерфейсе java.sql.CallableStatement.  
  
 Этот метод возвращает все числовые типы с помощью Java **float** точность.  
  
## <a name="see-also"></a>См. также:  
 [Метод getFloat &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

