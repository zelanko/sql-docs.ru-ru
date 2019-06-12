---
title: Метод getXAConnection () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXADataSource.getXAConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 75d45c751cc9350392fac7e6234ba13d294d6550
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801791"
---
# <a name="getxaconnection-method-"></a>Метод getXAConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает физическое соединение с базой данных, которое будет использоваться в распределенной транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект XAConnection.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод getXAConnection указывается с помощью метода getXAConnection в интерфейсе javax.sql.XADataSource.  
  
> [!NOTE]  
>  Этот метод обычно вызывается в реализациях пула соединений XA, а не в обычном коде приложений JDBC.  
  
## <a name="see-also"></a>См. также:  
 [Метод getXAConnection (SQLServerXADataSource)](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [Методы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Класс SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
