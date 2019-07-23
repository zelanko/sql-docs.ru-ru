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
ms.openlocfilehash: 87d7f85799524e3ac7c0e4d99608ce1d82b8f2fc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979930"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Метод getServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает значение свойства соединения **серверпрепаредстатементдискардсрешолд** . Этот параметр определяет, сколько невыполненных операций отмены подготовленной инструкции (sp_unprepare) может быть недоступно для каждого соединения, прежде чем будет выполнен вызов очистки необработанных дескрипторов на сервере. Если параметр имеет значение < = 1, то при закрытии подготовленных инструкций немедленно выполняются неподготовительные действия. Если задано значение > 1, эти вызовы объединяются в пакеты, чтобы избежать чрезмерных затрат на вызов sp_unprepare слишком часто. Значение по умолчанию для этого параметра можно изменить, вызвав Жетдефаултсерверпрепаредстатементдискардсрешолд ().

## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Возвращаемое значение
 Целое **число, содержащее** значение свойства соединения **серверпрепаредстатементдискардсрешолд** .

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6,4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
