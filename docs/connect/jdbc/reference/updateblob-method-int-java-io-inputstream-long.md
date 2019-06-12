---
title: Метод updateBlob (int, java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2edf9b51-63e1-4c28-afdf-2d4af593d5f7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7dbb398a1b280b413739b4464d859e85cc7d6811
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787262"
---
# <a name="updateblob-method-int-javaioinputstream-long"></a>Метод updateBlob (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец из заданного входного потока, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBlob(int columnIndex,  
                       java.io.InputStream inputStream,  
                                              long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *inputStream*  
  
 Объект, InputStream.  
  
 *length*  
  
 Значение типа **long**, указывающее длину потока.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBlob указывается с помощью метода updateBlob в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBlob (SQLServerResultSet)](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
