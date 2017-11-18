---
title: "Метод getURL (int) | Документы Microsoft"
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
- SQLServerCallableStatement.getURL Ijnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 75d03ced-3614-4997-9abd-24642b1d1aae
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 89feb3812a54d9c651d7fd36a07886d94782290d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="geturl-method-int"></a>Метод getURL (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде URL-адрес объекта в языке программирования Java по заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.net.URL getURL(int n)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект URL-адрес.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getURL указывается с помощью метода getURL в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getURL &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

