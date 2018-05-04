---
title: getServerPreparedStatementDiscardThreshold метод (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9281981535d24187e8408313e13264627720cd45
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>getServerPreparedStatementDiscardThreshold метод (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение **serverPreparedStatementDiscardThreshold** свойство соединения. Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр имеет значение < = 1 аннулирующие действия выполняются немедленно для подготовленной инструкции close. Если это значение равно > 1 эти вызовы группируются вместе, чтобы избежать вызова sp_unprepare слишком часто.

  
## <a name="syntax"></a>Синтаксис  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **int** значение **serverPreparedStatementDiscardThreshold** свойство соединения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Замечания  
 Этот метод доступен из драйвера JDBC версии 6.4 и далее.
 
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
