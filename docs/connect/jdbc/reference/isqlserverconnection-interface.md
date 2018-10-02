---
title: Интерфейс ISQLServerConnection | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a7087b01ed04d176faa1d2863813fcb9bcf0de0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759232"
---
# <a name="isqlserverconnection-interface"></a>Интерфейс ISQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет подключение JDBC к базе данных [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Этот интерфейс добавлен в версии 3.0 драйвера JDBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет**: java.sql.Connection  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>Remarks  
 Этот интерфейс реализуется [класса SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Этот интерфейс обеспечивает доступ к следующим полям, определяемым [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
|Поле|Дополнительные сведения см. в разделе|  
|-----------|-------------------------------|  
|public final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|public UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
