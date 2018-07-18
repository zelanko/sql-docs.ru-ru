---
title: Класс SQLServerXAConnection | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6563ca27d1e2abfbabf30374e410cdd970651d34
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846349"
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
  
  
