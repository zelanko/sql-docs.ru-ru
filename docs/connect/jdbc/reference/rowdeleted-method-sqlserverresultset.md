---
title: Метод (SQLServerResultSet) rowDeleted | Документы Microsoft
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
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49dc624ba683d41f527780c69204aadd9b2a51b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] выявляет удаленные строки для всех обновляемых типов курсора, хотя обнаружение является временным для однопроходных и динамических курсоров.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
