---
description: Метод setAsciiStream (java.lang.String, java.io.InputStream, long)
title: Метод setAsciiStream для реализации входного потока данных (long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6bc486cd-e432-4057-8789-9957ba23dd30
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbf55e2de65e6f3d4fd09d1ccd8305100e837f66
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432596"
---
# <a name="setasciistream-method-javalangstring-javaioinputstream-long"></a>Метод setAsciiStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанныйвходной поток, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setAsciiStream(java.lang.String parameterName,  
                                java.io.InputStream x,  
                                long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *x*  
  
 Объект InputStream.  
  
 *length*  
  
 Значение **long**, определяющее число байтов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setAsciiStream задается с помощью метода setAsciiStream в интерфейсе java.sql.PreparedStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если приложению нужно обновлять столбец из потока, длина которого неизвестна, рекомендуется для sqljdbc4.jar пользоваться методом JDBC 4.0 [setAsciiStream (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/setasciistream-method-java-lang-string-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [setAsciiStream (SQLServerCallableStatement)](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
