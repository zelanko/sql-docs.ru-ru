---
title: Метод rowInserted (SQLServerResultSet) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: da746533231983d67bbfe3689d0df63086d678bc
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765378"
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
 Этот метод rowUpdated указывается с помощью метода rowUpdated в интерфейсе java.sql.ResultSet.  
  
 Возвращаемое значение зависит от возможности обнаружения видимых операций вставки этим объектом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не обнаруживает вставленные строки ни для одного типа курсора.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
