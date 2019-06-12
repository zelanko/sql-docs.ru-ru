---
title: Метод isValid (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2868fb92161b5e3458e5c5e0dc72ebdef074b3e7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796318"
---
# <a name="isvalid-method-sqlserverconnection"></a>Метод isValid (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, верно ли, что этот объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) не закрыт и до сих пор действителен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *timeout*  
  
 Значение **int**, определяющее время ожидания (в секундах) при проверке соединения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если подключение является допустимым; **false**, если подключение не является допустимым или допустимость соединения не удается определить до завершения периода ожидания.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод isValid указывается с помощью метода isValid в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
