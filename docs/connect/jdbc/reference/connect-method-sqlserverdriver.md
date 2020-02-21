---
title: Метод connect (SQLServerDriver) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.connect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43813a4c-1cc7-4659-ba27-f1786f1371eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 518be09d4a4929a06866eec253a49a39d7865263
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955411"
---
# <a name="connect-method-sqlserverdriver"></a>Метод connect (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает соединение с базой данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Connection connect(java.lang.String Url,  
                                   java.util.Properties suppliedProperties)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Url*  
  
 Значение **String**, содержащее URL-адрес, который используется для подключения к базе данных.  
  
 *suppliedProperties*  
  
 Набор пар строковых значений, используемых как аргументы соединения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Connection.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод connect задается с помощью метода connect в интерфейсе java.sql.Driver.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Элементы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Класс SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
