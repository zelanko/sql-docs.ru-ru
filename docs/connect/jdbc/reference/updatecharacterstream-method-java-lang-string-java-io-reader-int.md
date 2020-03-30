---
title: Метод updateCharacterStream (java.io.Reader) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateCharacterStream (java.lang.String, java.io.Reader, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 08cfc4e0-83f0-4f2f-ac55-b381f34fe67f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20249faca3338a5f085de0e0071b20206b13dee1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67996751"
---
# <a name="updatecharacterstream-method-javalangstring-javaioreader-int"></a>Метод updateCharacterStream (java.lang.String, java.io.Reader, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец заданным значением символьного потока, который будет содержать указанное число символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateCharacterStream(java.lang.String columnName,  
                                  java.io.Reader readerValue,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
 *readerValue*  
  
 Объект Reader.  
  
 *length*  
  
 Значение типа **int**, указывающее длину потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateCharacterStream задается с помощью метода updateCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод передает символы Юникода от объекта средства чтения выбранным текстовым и двоичным столбцам. Сюда входят все текстовые и **двоичные** столбцы, а также столбцы **varbinary**, **varbinary(max)** , **image** и **xml**, но не входят столбцы **определяемых пользователем типов данных**.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. При использовании sqljdbc4.jar, если приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуем применять метод JDBC 4.0 [updateCharacterStream &#40;java.lang.String, java.io.Reader&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-java-lang-string-java-io-reader.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод updateCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
