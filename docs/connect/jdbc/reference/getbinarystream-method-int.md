---
title: Метод getBinaryStream (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c68917aefc39cce459a2de12f09ac75a35cf04b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920538"
---
# <a name="getbinarystream-method-int"></a>Метод getBinaryStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде двоичного потока неинтерпретированных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
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
  
  
