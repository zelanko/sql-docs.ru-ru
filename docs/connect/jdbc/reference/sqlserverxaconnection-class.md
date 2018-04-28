---
title: Класс SQLServerXAConnection | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1e095b498807412a40d4df1092b6c151c8c030c9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverxaconnection-class"></a>Класс SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет подключения JDBC, которые могут участвовать в распределенных транзакциях (XA).  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Реализует:** javax.sql.XAConnection  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Замечания  
 Можно прикрепить объекта SQLServerXAConnection в распределенной транзакции с помощью параметра [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) объекта. Диспетчер транзакций, обычно входящий в сервер среднего уровня, управляет объектом SQLServerXAConnection посредством объекта SQLServerXAResource.  
  
> [!NOTE]  
>  Программисты приложений обычно не используют этот интерфейс непосредственно. Он используется главным образом диспетчером транзакций, работающим на сервере среднего уровня.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
