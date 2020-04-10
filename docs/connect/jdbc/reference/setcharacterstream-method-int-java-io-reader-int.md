---
title: Метод setCharacterStream (int, java.io.Reader, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 139a5b74-8d7d-41cf-991a-a142349c58f6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e85062ff6902b7a39770f517fc61f920413e673
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929089"
---
# <a name="setcharacterstream-method-int-javaioreader-int"></a>Метод setCharacterStream (int, java.io.Reader, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру значение указанного объекта Reader, имеющего указанную длину в символах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCharacterStream(int n,  
                                     java.io.Reader reader,  
                                     int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 Значение **int**, определяющее номер параметра.  
  
 *reader*  
  
 Объект Reader.  
  
 *length*  
  
 Количество символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setCharacterStream задается с помощью метода setCharacterStream в интерфейсе java.sql.PreparedStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуется использовать метод JDBC 4.0 [setCharacterStream (int, java.io.Reader)](../../../connect/jdbc/reference/setcharacterstream-method-int-java-io-reader.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
