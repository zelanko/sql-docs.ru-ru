---
title: "Метод (SQLServerResultSet) rowUpdated | Документы Microsoft"
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
- SQLServerResultSet.rowUpdated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5f9b34859431b995ddfe6788b6eb08d6d9ed9d74
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="rowupdated-method-sqlserverresultset"></a>rowUpdated метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, была ли обновлена текущая строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если обе строки выполнено видимое обновление владельцем или другим пользователем, и обнаружены операции обновления. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод rowUpdated указывается с помощью метода rowUpdated в интерфейсе java.sql.ResultSet.  
  
 Возвращаемое значение зависит от возможности обнаружения операций обновления результирующим набором.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]не обнаруживает обновленные строки для любого типа курсора.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
