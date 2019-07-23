---
title: Метод getSendTimeAsDatetime (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1396ac28a7e41dbf530f7e4a251876f6c340871
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979947"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Метод getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в версии 3.0 драйвера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC.  
  
 Возвращает значение свойства соединения **сендтимеасдатетиме** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true** , если значения Java. SQL. Time будут отправляться на сервер в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] качестве типа **DateTime** . **значение false** , если значения Java. SQL. Time будут отправляться на сервер в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] качестве типа **времени** .  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о свойстве соединения **сендтимеасдатетиме** см. [в разделе Настройка свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md) .  
  
 [Метод SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) позволяет программным образом устанавливать свойство соединения **sendTimeAsDatetime**.  
  
 Дополнительные сведения см. в разделе [Настройка отправки значений Java. SQL. Time на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
