---
title: Класс SQLServerConnectionPoolDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bb073be8ef92d44f8821078f60622341638a010d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971649"
---
# <a name="sqlserverconnectionpooldatasource-class"></a>Класс SQLServerConnectionPoolDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет физические подключение к базе данных для диспетчеров пулов соединений.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
 **Реализует:** javax.sql.ConnectionPoolDataSource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerConnectionPoolDataSource обычно используется в средах Java Application Server, поддерживающих встроенные пулы соединений и требующих для установки физических соединений объект ConnectionPoolDataSource, например на серверах приложений платформы Java Enterprise Edition (Java EE), которые обеспечивают организацию пулов соединений по спецификациям JDBC 3.0 API.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
