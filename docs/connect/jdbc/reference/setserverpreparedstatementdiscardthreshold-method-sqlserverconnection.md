---
description: Метод setServerPreparedStatementDiscardThreshold (SQLServerConnection)
title: Метод setServerPreparedStatementDiscardThreshold (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca004a1eeb2e0446126673f4d500cdef092915dd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458346"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Метод setServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Указывает поведение для конкретного экземпляра подключения. Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого подключения, прежде чем на сервере будет выполнен вызов очистки незавершенных обработчиков. Когда этот параметр имеет значение не более 1, действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение больше 1, эти вызовы объединяются в пакет, чтобы избежать накладных расходов на частый вызов sp_unprepare.


## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Параметры  
 *thresholdValue*  
 
 Новое значение свойства подключения **serverPreparedStatementDiscardThreshold**.  
 
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
