---
title: getEnablePrepareOnFirstPreparedStatementCall метод (SQLServerDataSource) | Документы Microsoft
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
ms.openlocfilehash: 970d17947e4472feaea0bb95e6596d49455db1cf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 
## <a name="remarks"></a>Замечания  
 Этот метод доступен из драйвера JDBC версии 6.4 и далее.
 
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
