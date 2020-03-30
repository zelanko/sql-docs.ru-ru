---
title: Метод getXAConnection () | Документация Майкрософт
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
ms.openlocfilehash: 3c53cbcc5abcb9fb08999b1d171645b45097eb34
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977970"
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
 Этот метод getXAConnection задается с помощью метода getXAConnection в интерфейсе javax.sql.XADataSource.  
  
> [!NOTE]  
>  Этот метод обычно вызывается в реализациях пула соединений XA, а не в обычном коде приложений JDBC.  
  
## <a name="see-also"></a>См. также:  
 [Метод getXAConnection (SQLServerXADataSource)](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [Методы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Класс SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
