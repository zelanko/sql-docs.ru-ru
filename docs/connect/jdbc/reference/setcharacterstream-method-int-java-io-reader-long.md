---
title: Метод setCharacterStream (int, java.io.Reader, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cb6ac7f5-81ae-4cb7-87c8-cbee40d278c5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 67b28857940387b6feb7b2ce2bb2e7fed0eceff5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66795735"
---
# <a name="setcharacterstream-method-int-javaioreader-long"></a>Метод setCharacterStream (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру значение объекта java.io.Reader, имеющего указанную длину в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                                    java.io.Reader reader,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение **int**, определяющее номер параметра.  
  
 *reader*  
  
 Объект java.io.Reader, содержащий данные в Юникоде.  
  
 *length*  
  
 Значение **long**, которое указывает количество символов в потоке.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setCharacterStream указывается с помощью метода setCharacterStream в интерфейсе java.sql.PreparedStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуется использовать метод JDBC 4.0 [setCharacterStream (int, java.io.Reader)](../../../connect/jdbc/reference/setcharacterstream-method-int-java-io-reader.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setCharacterStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
