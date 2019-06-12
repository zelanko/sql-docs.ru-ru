---
title: Метод createClob (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: add9cb59748ce4de615ec4ac73117984bb2c8642
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66795569"
---
# <a name="createclob-method-sqlserverconnection"></a>Метод createClob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект Clob, не содержащий данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Clob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод createClob указывается с помощью метода createClob в интерфейсе java.sql.Connection.  
  
 Этот метод исключает необходимость в [конструктор SQLServerClob &#40;SQLServerConnection, java.lang.String&#41;](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
