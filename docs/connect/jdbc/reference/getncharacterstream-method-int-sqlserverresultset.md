---
title: Метод getNCharacterStream (int) (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f1cfa4e4-3e1f-4504-b0de-cc626d653661
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 346039437c56c249bb4d030df5f9235aaf666331
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732550"
---
# <a name="getncharacterstream-method-int-sqlserverresultset"></a>Метод getNCharacterStream (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Reader getNCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект средства чтения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getNCharacterStream указывается с помощью метода getNCharacterStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод можно использовать для извлечения значения **nvarchar**, **nchar**, **nvarchar(max)**, **ntext**, или **xml** столбца в текущей строке этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта. При попытке использования этого метода для получения значений других типов данных возникнет исключение.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNCharacterStream (SQLServerResultSet)](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
