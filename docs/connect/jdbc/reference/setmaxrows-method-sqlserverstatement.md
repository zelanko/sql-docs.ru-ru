---
title: "Метод setMaxRows (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b08d78a404c0454600072d9b227761d8c27045cc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setmaxrows-method-sqlserverstatement"></a>Метод setMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает ограничение на максимальное число строк, чтобы любое [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов могут содержать до указанного числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### <a name="parameters"></a>Параметры  
 *max*  
  
 **Int** , указывающее максимальное число строк, либо значение 0, если не ограничено.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setMaxRows указывается с помощью метода setMaxRows в интерфейсе java.sql.Statement.  
  
 Этот метод setMaxRows не оказывает влияния на динамические Прокручиваемые курсоры. В этом приложении следует с помощью синтаксиса SELECT TOP N SQL ограничивать число строк, возвращаемых из потенциально больших результирующих наборов.  
  
 При вызове метод setMaxRows [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] выполняет инструкции SET ROWCOUNT SQL при выполнении запроса приложения. В результате драйвер JDBC ограничивает максимальное число строк, затронутых всеми [!INCLUDE[tsql](../../../includes/tsql_md.md)] инструкций, выполняемых этим запросом, а не только количество строк, возвращаемых по этому запросу. Если приложению требуется ограничить только на верхнем уровне [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, его следует использовать синтаксис SQL SELECT TOP N в запросе, а не метод setMaxRows.  
  
 Дополнительные сведения об инструкции SET ROWCOUNT SQL см. в разделе «[SET ROWCOUNT (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=139522)» раздела [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

