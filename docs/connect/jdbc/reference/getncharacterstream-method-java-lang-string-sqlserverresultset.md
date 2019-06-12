---
title: Метод getNCharacterStream (java.lang.String) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a117f3a3-9c25-41e1-9adb-a40e90620dd6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 52e2f0336c2c4bfbe6b14ce116c0888844afc000
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784721"
---
# <a name="getncharacterstream-method-javalangstring-sqlserverresultset"></a>Метод getNCharacterStream (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getNCharacterStream(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Параметры  
 *ColumnLabel состоит из*  
  
 Значение String, содержащее метку столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект средства чтения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getNCharacterStream указывается с помощью метода getNCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод можно использовать для извлечения значения **nvarchar**, **nchar**, **nvarchar(max)** , **ntext**, или **xml** столбца в текущей строке этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта. При попытке использования этого метода для получения значений других типов данных возникнет исключение.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNCharacterStream (SQLServerResultSet)](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
