---
title: Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf48b4d280e9205a72025a346495f83aca68a064
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922401"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Указывает поведение для конкретного экземпляра соединения. Если значение равно false, первое выполнение вызывает sp_executesql и не подготавливает инструкцию, а второе выполнение вызывает sp_prepexec и фактически настраивает обработчик подготовленной инструкции. При всех последующих выполнениях вызывается sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>Параметры  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Новое значение свойства подключения **enablePrepareOnFirstPreparedStatementCall**.  
 
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
