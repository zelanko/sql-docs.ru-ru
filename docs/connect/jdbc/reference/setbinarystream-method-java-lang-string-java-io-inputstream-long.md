---
title: "Метод долго входным потоком: setBinaryStream | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d59c7327-c9dc-4e4f-9dff-19e1a3c62eb2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6abe3075cd884bdb69694bdf4072a5bcdad12ff0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setbinarystream-method-javalangstring-javaioinputstream-long"></a>Метод setBinaryStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный входной поток, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setBinaryStream(java.lang.String parameterName,  
                            java.io.InputStream x,  
                            long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *x*  
  
 Объект, InputStream.  
  
 *length*  
  
 Объект **длинные** , определяющее длину в байтах.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setBinaryStream указывается с помощью метода setBinaryStream в интерфейсе java.sql.CallableStatement.  
  
 Если длина потока отличается тем, что указывается в *длина* параметра, драйвер JDBC вызовет исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, *длина* параметра может быть задано значение -1, чтобы указать, что драйвер будет принимать потоки независимо от их длины. Для sqljdbc4.jar рекомендуется использовать метод JDBC 4.0 [метод setBinaryStream (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/setbinarystream-method-java-lang-string-java-io-inputstream.md) Если приложению нужно обновлять столбец из потока, длина которого неизвестна.  
  
## <a name="see-also"></a>См. также:  
 [setBinaryStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

