---
title: Метод setAsciiStream для входного потока, байт-int | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ea23386-201f-41af-8232-225de3476765
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f4ebed9ebad158ea445e726e8d0dbe0b60f57930
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975500"
---
# <a name="setasciistream-method--javalangstring-javaioinputstream-int"></a>Метод setAsciiStream (java.lang.String, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру заданный входной поток, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setAsciiStream(java.lang.String parameterName,  
                           java.io.InputStream value,  
                           int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *value*  
  
 Объект InputStream.  
  
 *length*  
  
 Значение типа **int**, определяющее длину номера в байтах.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setAsciiStream задается методом setAsciiStream в интерфейсе Java. SQL. CallableStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если приложению нужно обновлять столбец из потока, длина которого неизвестна, рекомендуется для sqljdbc4.jar пользоваться методом JDBC 4.0 [setAsciiStream (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/setasciistream-method-java-lang-string-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
