---
title: Метод getBinaryStream (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a0ee14b90dd8aaffb178c81ea46e5ec914752e28
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67953697"
---
# <a name="getbinarystream-method-javalangstring"></a>Метод getBinaryStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде двоичного потока неинтерпретированных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getBinaryStream задается с помощью метода getBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод можно использовать только с типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] binary, varbinary, varbinary(max) и image. Если использовать его с другими типами данных, будет вызвано исключение.  
  
 Значение, возвращенное этим методом в виде потока, можно считывать из потока отдельными фрагментами. Этот метод особенно удобен для получения больших значений LONGVARBINARY.  
  
> [!NOTE]  
>  Необходимо считать все данные в возвращенном потоке перед получением значения любого другого столбца. При следующем вызове метода считывания выполняется неявное закрытие потока. Кроме того, поток может возвращать значение 0, когда вызывается метод InputStream.available, независимо от наличия доступных данных.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBinaryStream (SQLServerResultSet)](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
