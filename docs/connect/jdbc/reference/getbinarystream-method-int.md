---
title: "Метод getBinaryStream (int) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.getBinaryStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f822af6387e66df4ed6f9a2fba28835220a6156
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getbinarystream-method-int"></a>Метод getBinaryStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде двоичного потока неинтерпретированных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getBinaryStream указывается с помощью метода getBinaryStream в интерфейсе java.sql.ResultSet.  
  
 Этот метод может использоваться только с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типы данных binary, varbinary, varbinary(max) и image. Если использовать его с другими типами данных, будет вызвано исключение.  
  
 Значение, возвращенное этим методом в виде потока, можно считывать из потока отдельными фрагментами. Этот метод особенно удобен для получения больших значений LONGVARBINARY.  
  
> [!NOTE]  
>  Необходимо считать все данные в возвращенном потоке перед получением значения любого другого столбца. При следующем вызове метода считывания выполняется неявное закрытие потока. Кроме того поток может возвращать значение 0 при вызове метода InputStream.available ли доступно данных или нет.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBinaryStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

