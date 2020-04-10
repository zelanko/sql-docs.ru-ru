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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 203ed2f6a68e11af8c63157a850a146ea8d81464
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80909603"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>Метод getEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает значение свойства подключения **enablePrepareOnFirstPreparedStatementCall**. Если это значение равно false, первое выполнение вызывает sp_executesql и не подготавливает инструкцию, а второе выполнение вызывает sp_prepexec и фактически настраивает обработчик подготовленной инструкции. При всех последующих выполнениях вызывается sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз. Значение по умолчанию для этого параметра можно изменить, вызвав setDefaultEnablePrepareOnFirstPreparedStatementCall().

## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Возвращаемое значение
 Возвращает **логическое** значение свойства подключения **enablePrepareOnFirstPreparedStatementCall**.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
