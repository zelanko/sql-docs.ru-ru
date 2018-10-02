---
title: Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e58e1a3814bd4fefda85f9ec525270923ef45dfe
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729922"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Задает поведение для определенного подключения экземпляра. Если значение равно false, во время первого выполнения будет вызывать sp_executesql и не Подготовка инструкции, после второго выполнения он будет вызывать sp_prepexec и настраивать дескриптором подготовленной инструкции. После выполнения вызовет sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>Параметры  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Новое значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения.  
 
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
