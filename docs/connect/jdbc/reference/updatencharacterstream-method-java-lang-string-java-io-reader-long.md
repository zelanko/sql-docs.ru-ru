---
title: Метод updateNCharacterStream (String - Reader - long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db0a96a8-248f-4664-9c13-f480f309ab91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ee869c9d9bdcc707456f1cb04b5dcacdacee89a0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67998688"
---
# <a name="updatencharacterstream-method-javalangstring-javaioreader-long"></a>Метод updateNCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением потока символов, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateNCharacterStream(java.lang.String columnLabel,  
                                    java.io.Reader reader,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение типа **String**, содержащее метку столбца.  
  
 *reader*  
  
 Объект Reader.  
  
 *length*  
  
 Длина потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateNCharacterStream задается с помощью метода updateNCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода из объекта Reader выбранным столбцам **nchar**, **nvarchar(max)** , **ntext** и **xml**. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если приложению нужно обновлять столбец из потока, длина которого неизвестна, рекомендуется для sqljdbc4.jar пользоваться методом JDBC 4.0 [updateNCharacterStream (java.lang.String, java.io.Reader)](../../../connect/jdbc/reference/updatencharacterstream-method-java-lang-string-java-io-reader.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateNCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
