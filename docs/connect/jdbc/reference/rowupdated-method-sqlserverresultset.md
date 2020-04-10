---
title: Метод rowUpdated (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowUpdated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c75169c8ea36ff4008e8a0237ffeaf9f9a9d0c5e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924503"
---
# <a name="rowupdated-method-sqlserverresultset"></a>Метод rowUpdated (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, была ли обновлена текущая строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если обнаружены операции обновления и при этом для строки выполнено видимое обновление владельцем или другим пользователем. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод rowUpdated задается с помощью метода rowUpdated в интерфейсе java.sql.ResultSet.  
  
 Возвращаемое значение зависит от возможности обнаружения операций обновления результирующим набором.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не обнаруживает обновленные строки ни для одного типа курсора.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
