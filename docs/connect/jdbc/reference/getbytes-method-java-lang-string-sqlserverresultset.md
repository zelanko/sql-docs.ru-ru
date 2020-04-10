---
title: Метод getBytes (java.lang.String) (SQLServerResultSet) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBytes (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ff617165-47f8-41c1-9c51-37ffc7714923
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5238b33eb48a011d06c6a38dcb96b7cc57b54d1b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921649"
---
# <a name="getbytes-method-javalangstring-sqlserverresultset"></a>Метод getBytes (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде массива типа **byte** на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public byte[] getBytes(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив значений типа **byte**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getBytes определен с помощью метода getBytes в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживает получение всех столбцов путем прямого считывания байтов с сервера. Он возвращает массив байтов непосредственно с сервера в формате, который хранится на сервере.  
  
 В предыдущей версии [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] метод SQLServerResultSet.getBytes мог преобразовывать значения из байтового массива в типы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**date**, **time**, **datetime2** или **datetimeoffset** и обратно. Теперь при вызове этого метода с такими типами данных возникает исключение, указывающее, что такое преобразование не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBytes (SQLServerResultSet)](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
