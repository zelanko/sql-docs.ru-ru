---
title: Метод updateBinaryStream (int, java.io.InputStream) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f84cfbe6-ebab-4357-8770-f1db34ecb04f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 619aa91a654656100d22ec806ba28e5e322338f6
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786739"
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
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуем использовать метод JDBC 4.0 [updateAsciiStream &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/updatebinarystream-method-int-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
