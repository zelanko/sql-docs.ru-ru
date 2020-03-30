---
title: Метод rowDeleted (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37221f0f9c7cf87576f0014b855ed28740e4818e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975712"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>Метод rowDeleted (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, была ли удалена строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если строка удалена и обнаружены операции удаления. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод rowDeleted задается с помощью метода rowDeleted в интерфейсе java.sql.ResultSet.  
  
 Удаленная строка может оставить заметный пробел в результирующем наборе. Этот метод позволяет обнаруживать пробелы в результирующем наборе. Возвращаемое значение зависит от возможности обнаружения операций удаления этим объектом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обнаруживает удаленные строки для всех обновляемых типов курсора, хотя обнаружение является временным для однопроходных и динамических курсоров.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
