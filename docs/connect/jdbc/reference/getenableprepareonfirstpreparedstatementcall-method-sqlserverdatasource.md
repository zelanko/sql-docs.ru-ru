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
ms.openlocfilehash: ce67d0e688ae3ad8909915d9906608f5370830b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983391"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>Метод getEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** . Если эта конфигурация возвращает значение false, то первое выполнение подготовленной инструкции вызывает процедуру sp_executesql, а не подготавливает инструкцию, после второго выполнения он вызывает sp_prepexec и фактически настраивает подготовленный обработчик инструкции. Следующие выполнения будут вызывать sp_execute. Это освобождает необходимость sp_unprepare при выполнении подготовленной инструкции Close, если инструкция выполняется только один раз. 
  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **логическое** значение свойства соединения **енаблепрепареонфирстпрепаредстатементкалл** .  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6,4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
