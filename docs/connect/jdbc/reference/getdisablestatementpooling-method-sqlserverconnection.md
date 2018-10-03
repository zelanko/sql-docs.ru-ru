---
title: Метод getDisableStatementPooling (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getDisableStatementPooling
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b939dcb1daf3e009e991fa5139c7f5edbe58a2d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733642"
---
# <a name="getdisablestatementpooling-method-sqlserverconnection"></a>Метод getDisableStatementPooling (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает значение **disableStatementPooling** свойство соединения. Этот параметр определяет, включен пул инструкции или не для этого подключения.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getDisableStatementPooling()  
```  

## <a name="return-value"></a>Возвращаемое значение
 Объект **логическое** , содержащий значение **disableStatementPooling** свойство соединения.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
