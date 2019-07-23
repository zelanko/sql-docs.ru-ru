---
title: Метод IsValid (SQLServerConnection) | Документация Майкрософт
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
ms.openlocfilehash: 3915690475e5ce9321af7fc15498c2bde018c640
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977137"
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
 Этот метод IsValid задается методом IsValid в интерфейсе Java. SQL. Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
