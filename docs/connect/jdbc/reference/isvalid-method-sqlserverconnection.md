---
title: Метод isValid (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 379d71b2100115bc1192a6f8f744b5afe92e5aed
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921088"
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
 Этот метод isValid задается с помощью метода isValid в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
