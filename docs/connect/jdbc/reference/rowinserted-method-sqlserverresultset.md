---
title: Метод (SQLServerResultSet) rowInserted | Документы Microsoft
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
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 224ee6eef64da19c76ccc3d65aa32c91f1636119
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, была ли сделана вставка в текущую строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если строка была выполнена вставка и обнаружены операции вставки. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод rowUpdated указывается с помощью метода rowUpdated в интерфейсе java.sql.ResultSet.  
  
 Значение, которое возвращается зависит это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) возможности обнаружения видимых операций вставки объектом.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] не обнаруживает вставленные строки для любого типа курсора.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
