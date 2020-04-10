---
title: Метод setAsciiStream (int, java.io.InputStream, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9436c39f-f1a1-484a-a75b-776a72ca70f4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0db1f78923cd7c91c6b94061a2d2ac9451f22974
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920198"
---
# <a name="setasciistream-method-int-javaioinputstream-int"></a>Метод setAsciiStream (int, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер назначенного параметра для указанного объекта InputStream с указанным числом байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setAsciiStream(int n,  
                                 java.io.InputStream x,  
                                 int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 Значение **int**, определяющее номер параметра.  
  
 *x*  
  
 Объект InputStream.  
  
 *length*  
  
 Число байтов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setAsciiStream задается с помощью метода setAsciiStream в интерфейсе java.sql.PreparedStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуем использовать метод JDBC 4.0 [setAsciiStream (int, java.io.InputStream)](../../../connect/jdbc/reference/setasciistream-method-int-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setAsciiStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
