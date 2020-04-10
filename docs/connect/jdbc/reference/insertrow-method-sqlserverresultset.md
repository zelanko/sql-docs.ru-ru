---
title: Метод insertRow (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 194df3470eead10c0f32288f54b36a82e807e576
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80909930"
---
# <a name="insertrow-method-sqlserverresultset"></a>Метод insertRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Добавляет содержимое строки вставки в этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) и в базу данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод insertRow определен с помощью метода insertRow в интерфейсе java.sql.ResultSet.  
  
 В момент вызова этого метода курсор должен располагаться в строке вставки. После вызова этого метода курсор остается в строке вставки, а результирующий набор остается в режиме вставки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
