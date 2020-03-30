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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979947"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Метод getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в версии 3.0 драйвера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC.  
  
 Возвращает значение свойства подключения **sendTimeAsDatetime**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если значения java.sql.Time будут отправляться на сервер с типом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime**. **false**, если значения java.sql.Time будут отправляться на сервер с типом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **time**.  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения о свойстве подключения [sendTimeAsDatetime](../../../connect/jdbc/setting-the-connection-properties.md) см. в статье о **настройке свойств подключения**.  
  
 [Метод SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) позволяет программным образом устанавливать свойство соединения **sendTimeAsDatetime**.  
  
 Дополнительные сведения см. в статье [Настройка способа отправки значений java.sql.Time на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
