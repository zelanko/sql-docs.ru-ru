---
title: Метод getQueryTimeout (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c513265-cd0c-4b38-9494-94458c17a16d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9a4a271e07dea5a533dcb19b098a3e3de29e535e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973181"
---
# <a name="setquerytimeout-method-sqlserverstatement"></a>Метод getQueryTimeout (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает время в секундах, в течение которого драйвер будет ожидать выполнения объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setQueryTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>Параметры  
 *секунд*  
  
 Значение типа **int**, указывающее продолжительность ожидания в секундах. Значение 0 показывает, что ожидание неограниченно.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setQueryTimeout задается с помощью метода setQueryTimeout в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
