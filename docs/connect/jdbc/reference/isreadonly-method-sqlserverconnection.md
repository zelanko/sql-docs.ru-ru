---
title: Метод isReadOnly (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isReadOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 902fd2c1-05e0-436e-9779-c048cdb8475a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 708060b6192e47a126c9c4c3ea47052c098bb1fd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977320"
---
# <a name="isreadonly-method-sqlserverconnection"></a>Метод isReadOnly (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, находится ли этот объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) в режиме только для чтения.  
  
> [!NOTE]  
>  Сейчас этот метод не поддерживается [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isReadOnly()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если соединение выполняется в режиме только для чтения; значение **false**, если это не так.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод isReadOnly задается с помощью метода isReadOnly в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
