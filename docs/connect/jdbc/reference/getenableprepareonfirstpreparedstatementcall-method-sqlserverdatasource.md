---
title: "getEnablePrepareOnFirstPreparedStatementCall метод (SQLServerDataSource) | Документы Microsoft"
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
ms.openlocfilehash: 766a00c0a92c3df65e39bbfcd7ad87c5529a5b98
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall метод (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения. Эта конфигурация возвращает значение false первого выполнения подготовленной инструкции вызовите процедуры sp_executesql и не Подготовка инструкции, после второго выполнения происходит его вызывает sp_prepexec и фактически установки дескриптор подготовленной инструкции. После выполнения вызывает sp_execute. Это избавляет от для sp_unprepare для подготовленной инструкции close, если инструкция выполняется только один раз. 
  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **логическое** значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6.4 и далее.
 
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
