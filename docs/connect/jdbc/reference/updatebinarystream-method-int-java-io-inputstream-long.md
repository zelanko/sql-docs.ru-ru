---
title: Метод updateBinaryStream (int, java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f84cfbe6-ebab-4357-8770-f1db34ecb04f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1b610372ddf3d435b34ec065b26a35de5f18a000
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798856"
---
# <a name="updatebinarystream-method-int-javaioinputstream-long"></a>Метод updateBinaryStream (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение двоичного потока в указанном столбце, в котором указывается заданное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x,  
                               long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект, InputStream.  
  
 *length*  
  
 Значение типа **long**, указывающее длину потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBinaryStream указывается с помощью метода updateBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает байты от объекта InputStream выбранным двоичным столбцам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], таким как binary, varbinary, varbinary(max), image, xml и udt. В этом методе не поддерживается обновление символьных столбцов. Для обновления с помощью InputStream символьных столбцов используйте метод [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md).  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если приложению нужно обновлять столбец из потока, длина которого неизвестна, рекомендуется для sqljdbc4.jar пользоваться методом JDBC 4.0 [updateBinaryStream (int, java.io.InputStream)](../../../connect/jdbc/reference/updatebinarystream-method-int-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
