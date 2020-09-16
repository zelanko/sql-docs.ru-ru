---
description: Метод setServerPreparedStatementDiscardThreshold (SQLServerDataSource)
title: Метод setServerPreparedStatementDiscardThreshold (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: dfef943dda60696d9764466df2e880acad1e3d04
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458343"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>Метод setServerPreparedStatementDiscardThreshold (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение свойства подключения serverPreparedStatementDiscardThreshold. Этот параметр определяет, сколько невыполненных операций отмены для подготовленных инструкций (sp_unprepare) допускается для каждого подключения, прежде чем на сервере будет выполнен вызов очистки незавершенных обработчиков. Когда этот параметр имеет значение не более 1, действия аннулирования выполняются немедленно после завершения подготовленной инструкции. Если задано значение больше 1, эти вызовы объединяются в пакет, чтобы избежать накладных расходов на частый вызов sp_unprepare.
 
## <a name="syntax"></a>Синтаксис  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Параметры  
 *serverPreparedStatementDiscardThreshold*  
  
 Новое значение свойства подключения **serverPreparedStatementDiscardThreshold**.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
