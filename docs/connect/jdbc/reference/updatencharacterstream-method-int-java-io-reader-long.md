---
title: Метод updateNCharacterStream (int, java.io.Reader, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: aeec0a56-038e-45b1-98c8-b1046ebd25db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 03d1ea61a0f14baed7e83e27fbc585c96ee0e2ab
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67998756"
---
# <a name="updatencharacterstream-method-int-javaioreader-long"></a>Метод updateNCharacterStream (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением потока символов, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNCharacterStream(int columnIndex,  
                                    java.io.Reader x,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект Reader.  
  
 *length*  
  
 Длина потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNCharacterStream задается с помощью метода updateNCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода из объекта Reader выбранным столбцам типа **nchar**, **nvarchar(max)** , **ntext** или **xml** Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. При использовании sqljdbc4.jar, если приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуется применять метод JDBC 4.0 [updateNCharacterStream (int, java.io.Reader)](../../../connect/jdbc/reference/updatencharacterstream-method-int-java-io-reader.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
