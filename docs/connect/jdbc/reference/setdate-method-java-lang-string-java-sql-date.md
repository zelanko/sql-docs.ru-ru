---
title: "Строковое значение даты - метод setDate метод setDate | Документы Microsoft"
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
- SQLServerCallableStatement.setDate (java.lang.String, java.sql.Date)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4762e2bd-5e94-4562-97d5-f023ecffc08c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d0663f5469b00f0bc3d9db3e1817f06894b53aca
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setdate-method-javalangstring-javasqldate"></a>Метод setDate (java.lang.String, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру заданное значение даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setDate(java.lang.String sCol,  
                    java.sql.Date d)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *d*  
  
 Объект Date.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setDate указывается с помощью метода setDate в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

