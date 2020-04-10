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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e3e8f4cdd1ae9d0fcb61ab5ccb2c47c11fb52ef
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925120"
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
  
  
