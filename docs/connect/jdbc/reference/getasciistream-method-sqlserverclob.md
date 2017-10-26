---
title: "Метод getAsciiStream (SQLServerClob) | Документы Microsoft"
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
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4025d8814415e0889168bba781254a736d504260
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getasciistream-method-sqlserverclob"></a>Метод getAsciiStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Материализует объект CLOB в виде потока ASCII.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Входной поток, содержащий данные объекта CLOB.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getAsciiStream указывается с помощью метода getAsciiStream в интерфейсе java.sql.Clob.  
  
 Всегда возвращает поток байтов и предполагает, что данные в объекте CLOB имеют формат ASCII, поскольку нет возможности узнать, что данные используют Юникод или другую многобайтовую кодировку страницы.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  

