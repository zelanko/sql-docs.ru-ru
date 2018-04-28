---
title: Метод setMaxRows (SQLServerStatement) | Документы Microsoft
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
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f697921ebeb05416555495197812e818a2d1058e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
