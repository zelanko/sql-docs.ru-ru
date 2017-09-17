---
title: "Метод executeUpdate (java.lang.String, java.lang.String) | Документы Microsoft"
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
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 53682225a680d9913fd03e4e7a52beee729eecbc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>Метод executeUpdate (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и сигналы [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] что автоматически сформированные ключи, указанная в заданном массиве должны быть доступны для загрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Параметры  
 *SQL*  
  
 Объект **строка** , содержащий инструкции SQL.  
  
 *columnNames*  
  
 Массив объектов типа **строка** , указывающее, какие имена столбцов автоматически сформированных ключей должны быть доступными.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее количество затронутых строк, 0 для инструкций DDL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод executeUpdate указывается с помощью метода executeUpdate в интерфейсе java.sql.Statement.  
  
 Если выполнение хранимой процедуры приведет к счетчика обновлений, больше единицы либо сформировано более одного результирующего набора, используйте [выполнение](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод для выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Метод executeUpdate &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
