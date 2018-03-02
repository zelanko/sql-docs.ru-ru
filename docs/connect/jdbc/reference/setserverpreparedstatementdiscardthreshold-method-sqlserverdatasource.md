---
title: "setServerPreparedStatementDiscardThreshold метод (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cbda72d00f8af453989e59f0591f519f872609c
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold метод (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение свойства соединения serverPreparedStatementDiscardThreshold. Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр имеет значение < = 1 аннулирующие действия выполняются немедленно для подготовленной инструкции close. Если значение равно > 1 эти вызовы объединяются вместе, чтобы избежать слишком часто вызова sp_unprepare
 
## <a name="syntax"></a>Синтаксис  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Параметры  
 *serverPreparedStatementDiscardThreshold*  
  
 Новое значение **serverPreparedStatementDiscardThreshold** свойство соединения.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6.4 и далее.
 
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
