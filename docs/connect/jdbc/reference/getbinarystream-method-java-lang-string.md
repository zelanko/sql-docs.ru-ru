---
title: Метод getBinaryStream (java.lang.String) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b0bf937f54db127721994053d7c40a2763d9a08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getbinarystream-method-javalangstring"></a>Метод getBinaryStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде двоичного потока неинтерпретированных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
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
  
## <a name="see-also"></a>См. также  
 [Метод getBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
