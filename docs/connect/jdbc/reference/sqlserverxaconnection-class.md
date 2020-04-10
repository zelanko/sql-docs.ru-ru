---
title: Класс SQLServerXAConnection | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5503084440427c43989a740e9197423fc5438aa
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926960"
---
# <a name="sqlserverxaconnection-class"></a>Класс SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет подключения JDBC, которые могут участвовать в распределенных транзакциях (XA).  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширение.** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Реализует:** javax.sql.XAConnection  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Remarks  
 Объект SQLServerXAConnection можно прикрепить в распределенной транзакции посредством объекта [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md). Диспетчер транзакций, обычно входящий в сервер среднего уровня, управляет объектом SQLServerXAConnection c помощью объекта SQLServerXAResource.  
  
> [!NOTE]  
>  Программисты приложений обычно не используют этот интерфейс непосредственно. Он используется главным образом диспетчером транзакций, работающим на сервере среднего уровня.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
