---
title: "Метод getBytes (java.lang.String) (SQLServerResultSet) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.getBytes (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ff617165-47f8-41c1-9c51-37ffc7714923
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba0880570009106ead7d9d3ea803e01b0b7d17fe
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getbytes-method-javalangstring-sqlserverresultset"></a>Метод getBytes (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **байтов** массива в языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public byte[] getBytes(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив **байтов** значения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getBytes указывается с помощью метода getBytes в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживает получение всех столбцов путем прямого считывания байтов с сервера. Он возвращает массив байтов непосредственно с сервера в формате, который хранится на сервере.  
  
 В предыдущей версии [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], можно использовать SQLServerResultSet.getBytes для преобразования значений между массивами байтов и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип данных **даты**, **время**, ** datetime2**, или **datetimeoffset**. Теперь при вызове этого метода с такими типами данных возникает исключение, указывающее, что такое преобразование не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBytes &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
