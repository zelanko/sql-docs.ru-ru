---
description: Метод setCharacterStream (int, java.io.Reader, long)
title: Метод setCharacterStream (int, java.io.Reader, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cb6ac7f5-81ae-4cb7-87c8-cbee40d278c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 669d9bbbf6f626a33c8162b789ddce719efbddcf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432286"
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
 Этот метод setCharacterStream задается с помощью метода setCharacterStream в интерфейсе java.sql.PreparedStatement.  
  
 Если длина потока отличается от указанной в параметре *length*, драйвер JDBC выдаст исключение при обновлении или вставке строки.  
  
 Если длина потока неизвестна, параметр *length* может иметь значение "–1", показывающее, что драйвер должен принимать поток любой длины. Если при использовании sqljdbc4.jar приложению нужно обновить столбец из потока, длина которого неизвестна, рекомендуется использовать метод JDBC 4.0 [setCharacterStream (int, java.io.Reader)](../../../connect/jdbc/reference/setcharacterstream-method-int-java-io-reader.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setCharacterStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
