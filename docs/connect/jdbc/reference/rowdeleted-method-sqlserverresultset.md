---
title: "Метод (SQLServerResultSet) rowDeleted | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.rowDeleted
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e4615318e2ca36d7524d25b0c5fcbf003711ee7
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, была ли удалена строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если строка удалена и обнаружены операции удаления. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод rowDeleted указывается с помощью метода rowDeleted в интерфейсе java.sql.ResultSet.  
  
 Удаленная строка может оставить заметный пробел в результирующем наборе. Этот метод позволяет обнаруживать пробелы в результирующем наборе. Значение, которое возвращается зависит это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект возможности обнаружения операций удаления.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]выявляет удаленные строки для всех обновляемых типов курсора, хотя обнаружение является временным для однопроходных и динамических курсоров.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
