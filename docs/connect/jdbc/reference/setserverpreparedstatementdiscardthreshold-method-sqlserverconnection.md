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
ms.openlocfilehash: 8f66746b15e96f49d96b428e8cf8844eeea12a12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972918"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Метод setServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Задает поведение для конкретного экземпляра соединения. Этот параметр определяет, сколько невыполненных операций отмены подготовленной инструкции (sp_unprepare) может быть недоступно для каждого соединения, прежде чем будет выполнен вызов очистки необработанных дескрипторов на сервере. Если параметр имеет значение < = 1, действия отмены подготовки выполняются немедленно при закрытии подготовленной инструкции. Если значение равно > 1, эти вызовы объединяются в пакеты, чтобы избежать чрезмерных затрат на вызов sp_unprepare слишком часто.


## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Параметры  
 *thresholdValue*  
 
 Новое значение свойства соединения **серверпрепаредстатементдискардсрешолд** .  
 
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6,4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
