---
description: Метод setAsciiStream (java.lang.String, java.io.InputStream, int)
title: setAsciiStream для реализации входного потока данных (int) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6edf6a538c0a2bf7f6f4783c5339277f622aac5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432606"
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
 Этот метод setAsciiStream задается с помощью метода setAsciiStream в интерфейсе java.sql.CallableStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если приложению нужно обновлять столбец из потока, длина которого неизвестна, рекомендуется для sqljdbc4.jar пользоваться методом JDBC 4.0 [setAsciiStream (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/setasciistream-method-java-lang-string-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
