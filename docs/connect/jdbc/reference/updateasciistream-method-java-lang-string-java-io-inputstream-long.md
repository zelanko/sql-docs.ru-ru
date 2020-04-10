---
title: Метод updateAsciiStream (java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d426e8b9-62b7-49f8-9863-8697fd3a7085
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33a0686a891a592f37a8ebd57f341df35db48894
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925568"
---
# <a name="updateasciistream-method-javalangstring-javaioinputstream-long"></a>Метод updateAsciiStream (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение ASCII-потока в указанном столбце, в котором указывается заданное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateAsciiStream(java.lang.String columnName,  
                              java.io.InputStream streamValue,  
                              long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
 *streamValue*  
  
 Объект InputStream.  
  
 *length*  
  
 Длина потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateAsciiStream задается с помощью метода updateAsciiStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает ASCII-символы (байты) из объекта InputStream в столбцы символьных значений, поддерживающие преобразование, то есть содержащие символы Юникода в диапазоне ASCII (от 0x00 до 0x7F) и соответствующие кодовым страницам 874, 932, 936, 949, 950 и с 1250 по 1258. Этот метод выполняет преобразование на целевую страницу параметров сортировки. Попытка обновления целевого столбца, не поддерживающего преобразование, приведет к возникновению исключения. В столбцах двоичных значений передаются необработанные байты.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуется использовать метод JDBC 4.0 [updateAsciiStream (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/updateasciistream-method-java-lang-string-java-io-inputstream.md) JDBC 4.0.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateAsciiStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
