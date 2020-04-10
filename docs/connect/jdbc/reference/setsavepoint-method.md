---
title: Метод setSavepoint () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c661df4fc5b60d52056c14bb9be1787a9a346fc0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924962"
---
# <a name="setsavepoint-method-"></a>Метод setSavepoint ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает в текущей транзакции безымянную точку сохранения и возвращает новый объект [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md), который ее представляет.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SavePoint.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setSavePoint определяется методом setSavePoint в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод setSavepoint (SQLServerConnection)](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
