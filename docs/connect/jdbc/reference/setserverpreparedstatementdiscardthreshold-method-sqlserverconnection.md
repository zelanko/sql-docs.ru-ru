---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: eddf7b58456a4730ff783ab4f53a9911da06d8db
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782972"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Метод setServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Задает поведение для определенного подключения экземпляра. Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр установлен в < = 1 un-Подготовка для подготовленной инструкции close действия выполняются немедленно. Если имеет значение > 1 эти вызовы будут объединены в один пакет, чтобы избежать вызова процедура sp_unprepare слишком часто.


## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Параметры  
 *thresholdValue*  
 
 Новое значение **параметр serverPreparedStatementDiscardThreshold** свойство соединения.  
 
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
