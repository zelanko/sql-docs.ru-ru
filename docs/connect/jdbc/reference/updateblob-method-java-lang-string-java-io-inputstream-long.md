---
title: Метод updateBlob (java.lang.String, java.io.InputStream, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 40f75549-5d5a-4de3-a271-4b8f0dd7b124
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1512bb2d20c62e30a1b35abde333abf14e595bdc
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787197"
---
# <a name="updateblob-method-javalangstring-javaioinputstream-long"></a>Метод updateBlob (java.lang.String, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец из заданного входного потока, который будет содержать указанное число байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBlob(java.lang.String columnLabel,  
                       java.io.InputStream inputStream)  
                                              long length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 Значение типа **String**, содержащее метку столбца.  
  
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
  
  
