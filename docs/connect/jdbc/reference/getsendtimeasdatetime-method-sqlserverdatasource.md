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
manager: jroth
ms.openlocfilehash: 36cdeda1cdad226c00449d118f154fd555e7246d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792084"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Метод getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в версии 3.0 драйвера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC.  
  
 Возвращает значение **sendTimeAsDatetime** свойство соединения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если значения java.sql.Time будут отправляться на сервер как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime** типа. **false** Если значения java.sql.Time будут отправляться на сервер как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **время** типа.  
  
## <a name="remarks"></a>Remarks  
 См. в разделе [заданию свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md) Дополнительные сведения о **sendTimeAsDatetime** свойство соединения.  
  
 [Метод SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) позволяет программным образом устанавливать свойство соединения **sendTimeAsDatetime**.  
  
 Дополнительные сведения см. в разделе [java.sql.Time настройке как значения отправляются на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
