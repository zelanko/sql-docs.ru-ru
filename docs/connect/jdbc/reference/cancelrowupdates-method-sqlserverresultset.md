---
title: Метод cancelRowUpdates (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.cancelRowUpdates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ecacca4-f7bc-4f5d-886a-da7747fdccae
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cdd669db96a3019915e7380aa6a450b2333de36e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780820"
---
# <a name="cancelrowupdates-method-sqlserverresultset"></a>Метод cancelRowUpdates (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Отменяет обновления текущей строки в этом объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void cancelRowUpdates()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод cancelRowUpdates указывается с помощью метода cancelRowUpdates в интерфейсе java.sql.ResultSet.  
  
 Этот метод можно вызывать после вызова метода адаптера и перед вызовом метода [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) для отката обновлений, выполненных в строке. Если обновления не выполнены или уже вызван метод updateRow, то этот метод не выполняет никаких действий.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
