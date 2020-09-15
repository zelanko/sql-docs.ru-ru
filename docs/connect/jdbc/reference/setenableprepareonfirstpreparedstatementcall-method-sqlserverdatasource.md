---
description: Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
title: Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 838696d89354d857c86aae0f6191d1dd08fba820
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431916"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает поведение для конкретного экземпляра подключения. Если значение равно false, первое выполнение подготовленной инструкции вызовет sp_executesql без подготовки инструкции, после второго выполнения будет вызван sp_prepexec и фактически настроен обработчик подготовленной инструкции. При всех последующих выполнениях вызывается sp_execute. Это избавляет от необходимости аннулировать закрываемую подготовленную инструкцию вызовом sp_unprepare, если эта инструкция выполнялась лишь один раз.  
## <a name="syntax"></a>Синтаксис  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Параметры  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Новое значение свойства подключения **enablePrepareOnFirstPreparedStatementCall**.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
