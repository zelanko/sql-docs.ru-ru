---
title: "Метод setNCharacterStream объект чтения - long | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af9a1ba8-7980-43fa-88e5-14f6cc5e897c
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f47eb454958dce0e41a3f864c54581b202f44e1c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setncharacterstream-method-javalangstring-javaioreader-long"></a>Метод setNCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект чтения, равен указанному числу символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                     java.io.Reader value,  
                     long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , указывающее имя параметра.  
  
 *value*  
  
 Объект модуля чтения.  
  
 *length*  
  
 Объект **длинные** указывает число символов в поток.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setNCharacterStream указывается с помощью метода setNCharacterStream в интерфейсе java.sql.CallableStatement.  
  
 Этот метод следует использовать для **NCHAR**, **NVARCHAR**, **NTEXT**, и **XML** типов данных.  
  
 Если длина потока отличается тем, что указывается в *длина* параметра, драйвер JDBC вызовет исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, *длина* параметра может быть задано значение -1, чтобы указать, что драйвер будет принимать потоки независимо от их длины. Для sqljdbc4.jar рекомендуется использовать метод JDBC 4.0 [setNCharacterStream метод &#40;java.lang.String, java.io.Reader &#41;](../../../connect/jdbc/reference/setncharacterstream-method-java-lang-string-java-io-reader.md) Если приложению нужно обновлять столбец из потока, длина которого совпадает с Неизвестный.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNCharacterStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
