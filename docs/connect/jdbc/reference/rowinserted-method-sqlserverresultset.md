---
title: Метод rowInserted (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5b471631bb5111f6bc6af5889ecf0d4444e4742c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903892"
---
# <a name="rowinserted-method-sqlserverresultset"></a>Метод rowInserted (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, была ли сделана вставка в текущую строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если в строке выполнена вставка и обнаружены операции вставки. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод rowUpdated задается с помощью метода rowUpdated в интерфейсе java.sql.ResultSet.  
  
 Возвращаемое значение зависит от возможности обнаружения видимых операций вставки этим объектом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не обнаруживает вставленные строки ни для одного типа курсора.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
