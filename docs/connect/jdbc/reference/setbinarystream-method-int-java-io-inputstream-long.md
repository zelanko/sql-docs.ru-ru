---
title: Метод setBinaryStream (int, java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4ab2e2f3-eaf0-471a-8422-2cf98ce979cf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 712fdfd5cd4b7dd87654d78feea49b15278bdd02
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921226"
---
# <a name="setbinarystream-method-int-javaioinputstream-long"></a>Метод setBinaryStream (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Присваивает указанному параметру указанный входной поток, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setBinaryStream(int parameterIndex,  
                                 java.io.InputStream x,  
                                          long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение **int**, определяющее номер параметра.  
  
 *x*  
  
 Объект java.io.InputStream.  
  
 *length*  
  
 Значение **long**, определяющее число байтов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setBinaryStream задается с помощью метода setBinaryStream в интерфейсе java.sql.PreparedStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуется использовать метод JDBC 4.0 [setBinaryStream Method (int, java.io.InputStream)](../../../connect/jdbc/reference/setbinarystream-method-int-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setBinaryStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
