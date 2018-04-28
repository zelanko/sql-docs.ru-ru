---
title: Метод (java.io.InputStream, long) updateBinaryStream | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3c0fb5d-ca05-43f7-9f38-fba6cf3705c6
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05b0c55c1b8985592b42f3055b994dce35c6b746
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="updatebinarystream-method-javalangstring-javaioinputstream-long"></a>Метод updateBinaryStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение двоичного потока в указанном столбце, в котором указывается заданное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBinaryStream(java.lang.String columnLabel,  
                               java.io.InputStream x,  
                               long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 AStringthat содержит метку столбца.  
  
 *x*  
  
 Объект, InputStream.  
  
 *длина*  
  
 Объект **длинные** , указывающее длину потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateBinaryStream указывается с помощью метода updateBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает байты от объекта InputStream для выбранных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] двоичных столбцов, таких как binary, varbinary, varbinary(max), изображение, xml и определяемого пользователем типа. В этом методе не поддерживается обновление символьных столбцов. Чтобы обновить символьный столбец с InputStream, используйте [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) метод.  
  
 Если длина потока отличается тем, что указывается в *длина* параметра, драйвер JDBC вызовет исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, *длина* параметра может быть задано значение -1, чтобы указать, что драйвер будет принимать потоки независимо от их длины. Для sqljdbc4.jar рекомендуется использовать метод JDBC 4.0 [метод updateBinaryStream &#40;java.lang.String, java.io.InputStream&#41; ](../../../connect/jdbc/reference/updatebinarystream-method-java-lang-string-java-io-inputstream.md) Если приложению нужно обновлять столбец из потока, длина которого совпадает с Неизвестный.  
  
## <a name="see-also"></a>См. также  
 [Метод updateBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
