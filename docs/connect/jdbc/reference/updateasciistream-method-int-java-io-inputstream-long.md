---
title: Метод updateAsciiStream (java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 143bff3e-2b5c-485d-9529-1c2387560094
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3e75b36daaccb0526674da64591b409f5c9856e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985510"
---
# <a name="updateasciistream-method-int-javaioinputstream-long"></a>Метод updateAsciiStream (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет значение ASCII-потока в указанном столбце, в котором указывается заданное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateAsciiStream(int columnIndex,  
                              java.io.InputStream x,  
                              long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект InputStream.  
  
 *length*  
  
 Длина потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateAsciiStream задается методом updateAsciiStream в интерфейсе Java. SQL. Result.  
  
 Этот метод передает ASCII-символы (байты) из объекта InputStream в столбцы символьных значений, поддерживающие преобразование, то есть содержащие символы Юникода в диапазоне ASCII (от 0x00 до 0x7F) и соответствующие кодовым страницам 874, 932, 936, 949, 950 и с 1250 по 1258. Этот метод выполняет преобразование на целевую страницу параметров сортировки. Попытка обновления целевого столбца, не поддерживающего преобразование, приведет к возникновению исключения. В столбцах двоичных значений передаются необработанные байты.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуем использовать метод JDBC 4.0 [updateAsciiStream &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/updateasciistream-method-int-java-io-inputstream.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateAsciiStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
