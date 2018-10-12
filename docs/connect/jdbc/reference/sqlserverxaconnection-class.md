---
title: Класс SQLServerXAConnection | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f2cc7956f36ee6fad113efd1cfe5afd5f58baff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782992"
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
  
## <a name="remarks"></a>Remarks  
 Объект SQLServerXAConnection можно прикрепить в распределенной транзакции посредством объекта [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md). Диспетчер транзакций, обычно входящий в сервер среднего уровня, управляет объектом SQLServerXAConnection посредством объекта SQLServerXAResource.  
  
> [!NOTE]  
>  Программисты приложений обычно не используют этот интерфейс непосредственно. Он используется главным образом диспетчером транзакций, работающим на сервере среднего уровня.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
