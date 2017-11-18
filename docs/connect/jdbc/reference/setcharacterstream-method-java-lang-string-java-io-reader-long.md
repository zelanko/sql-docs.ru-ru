---
title: "Метод setCharacterStream (java.lang.String, java.io.Reader, long) | Документы Microsoft"
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
ms.assetid: 54fb2f13-f8d8-47b5-bec1-4a5af3e86a84
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2eb07858fbadae5433c4675386b74383740ca694
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setcharacterstream-method-javalangstring-javaioreader-long"></a>Метод setCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный java.io.Reader объекту, который имеет указанное число символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *Модуль чтения*  
  
 Объект чтения, содержащего данные Юникода.  
  
 *length*  
  
 Объект **длинные** указывает число символов в поток.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setCharacterStream указывается с помощью метода setCharacterStream в интерфейсе java.sql.CallableStatement.  
  
 Если длина потока отличается тем, что указывается в *длина* параметра, драйвер JDBC вызовет исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, *длина* параметра может быть задано значение -1, чтобы указать, что драйвер будет принимать потоки независимо от их длины. Для sqljdbc4.jar рекомендуется использовать метод JDBC 4.0 [метод setCharacterStream (java.lang.String, java.io.Reader)](../../../connect/jdbc/reference/setcharacterstream-method-java-lang-string-java-io-reader.md) Если приложению нужно обновлять столбец из потока, длина которого неизвестна.  
  
## <a name="see-also"></a>См. также:  
 [Метод setCharacterStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

