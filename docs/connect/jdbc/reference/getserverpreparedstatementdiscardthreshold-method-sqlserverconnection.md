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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 844f4574fa7a0a45c772a3ac3eff57bb91f23c3b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925360"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>Метод getServerPreparedStatementDiscardThreshold (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает значение свойства подключения **serverPreparedStatementDiscardThreshold**. Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого соединения, прежде чем на сервере будет выполнен вызов очистки необработанных дескрипторов. Если этот параметр имеет значение не более 1, то действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение более 1, такие вызовы объединяются в пакет, чтобы снизить накладные расходы на частый вызов sp_unprepare. Значение по умолчанию для этого параметра можно изменить, вызывая метод getDefaultServerPreparedStatementDiscardThreshold().

## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Возвращаемое значение
 Значение **int** со свойством подключения **serverPreparedStatementDiscardThreshold**.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
