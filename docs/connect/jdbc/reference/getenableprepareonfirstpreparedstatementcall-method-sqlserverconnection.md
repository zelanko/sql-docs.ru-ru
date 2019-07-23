---
title: Метод getEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ac1cf4dbd8c8c14b5c97dbfecbe81d397c1598ce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983442"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>Метод getEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** . Если значение равно false, первое выполнение будет вызывать процедуру sp_executesql, а не подготавливать инструкцию, после второго выполнения он вызовет sp_prepexec и фактически настроит подготовленный обработчик инструкции. Следующие выполнения будут вызывать sp_execute. Это освобождает необходимость sp_unprepare при выполнении подготовленной инструкции Close, если инструкция выполняется только один раз. Значение по умолчанию для этого параметра можно изменить, вызвав Сетдефаултенаблепрепареонфирстпрепаредстатементкалл ().

## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Возвращаемое значение
 **Логическое** значение, содержащее свойство соединения **енаблепрепареонфирстпрепаредстатементкалл** .

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6,4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
