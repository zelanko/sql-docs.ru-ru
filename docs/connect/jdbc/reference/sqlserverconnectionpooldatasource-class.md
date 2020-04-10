---
title: Класс SQLServerConnectionPoolDataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0accd21f53a4ba1a86e4b7555be9d2ba9a087474
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921050"
---
# <a name="sqlserverconnectionpooldatasource-class"></a>Класс SQLServerConnectionPoolDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет физические подключение к базе данных для диспетчеров пулов соединений.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширение:** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
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
  
  
