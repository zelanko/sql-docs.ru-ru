---
title: Метод getServerPreparedStatementDiscardThreshold (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 22f7bf637d20b42a7dadd3397e84c826fa277a22
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66791922"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Метод getServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает значение **параметр serverPreparedStatementDiscardThreshold** свойство соединения. Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр может быть < = 1, unprepare для подготовленной инструкции close действия выполняются немедленно. Если он имеет значение > 1, эти вызовы будут объединены в один пакет во избежание издержки вызове процедура sp_unprepare слишком часто. Значение по умолчанию для этого параметра можно изменить, вызывающий getDefaultServerPreparedStatementDiscardThreshold().

## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Возвращаемое значение
 **Int** , содержащий значение **параметр serverPreparedStatementDiscardThreshold** свойство соединения.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
