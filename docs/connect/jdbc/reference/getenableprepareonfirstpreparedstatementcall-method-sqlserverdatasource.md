---
title: Метод getEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 721e19f1a4941cacfd18e04a14e6fa6d851cde60
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667523"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>Метод getEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения. Если эта конфигурация возвращает значение false первого выполнения подготовленной инструкции вызова sp_executesql и не Подготовка инструкции, после второго выполнения он будет вызывать sp_prepexec и фактически установки дескриптором подготовленной инструкции. После выполнения вызовет sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз. 
  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **логическое** значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
