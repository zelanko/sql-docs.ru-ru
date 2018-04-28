---
title: Метод executeUpdate (java.lang.String, int[]) | Документы Microsoft
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
ms.topic: article
apiname:
- SQLServerStatement.executeUpdate (java.lang.String, int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b3d5b60-4285-4047-b13e-106754ca0d98
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fb2372d8ae0da672430c2817a29a6c440b0817a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="executeupdate-method-javalangstring-int"></a>Метод executeUpdate (java.lang.String, int[])
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и сигналы [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] что автоматически сформированные ключи, отмеченные в заданном массиве должны быть доступны для загрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               int[] columnIndexes)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Объект **строка** , содержащий инструкции SQL.  
  
 *columnIndexes*  
  
 Массив значений int, указывающих индексы столбцов автоматически сформированных ключей, которые должны быть доступными.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** указывает число обработанных строк, либо значение 0 для инструкций DDL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод executeUpdate указывается с помощью метода executeUpdate в интерфейсе java.sql.Statement.  
  
 Если выполнение хранимой процедуры приведет к счетчика обновлений, больше единицы либо сформировано более одного результирующего набора, используйте [выполнение](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод для выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Метод executeUpdate &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
