---
title: "Метод setNCharacterStream для объекта java.io.Reader - long | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36396dc9-f109-4da0-bd64-726704046bbf
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1659f34537ae65aabb505ff01fa9796ec558a3de
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setncharacterstream-method-int-javaioreader-long"></a>Метод setNCharacterStream (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный объект модуля чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNCharacterStream(int parameterIndex,  
                                                  java.io.Reader value,  
                                                                long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 **Int** , указывающее индекс параметра.  
  
 *value*  
  
 Объект средства чтения, который содержит значение параметра.  
  
 *length*  
  
 Объект **длинные** указывает число символов в значении параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setNCharacterStream указывается с помощью метода setNCharacterStream в интерфейсе java.sql.PreparedStatement.  
  
 Этот метод следует использовать для **NCHAR**, **NVARCHAR**, **NTEXT**, и **XML** типов данных.  
  
 Если длина потока отличается тем, что указывается в *длина* параметра, драйвер JDBC вызовет исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, *длина* параметра может быть задано значение -1, чтобы указать, что драйвер будет принимать потоки независимо от их длины. Для sqljdbc4.jar рекомендуется использовать метод JDBC 4.0 [setNCharacterStream метод &#40; int, java.io.Reader &#41;](../../../connect/jdbc/reference/setncharacterstream-method-int-java-io-reader.md) Если приложению нужно обновлять столбец из потока, длина которого неизвестна.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNCharacterStream &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  

