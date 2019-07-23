---
title: Метод getServerPreparedStatementDiscardThreshold (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: 3f91b75b5c70029d53582b8b6ed4655485fd3fcf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979903"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>Метод getServerPreparedStatementDiscardThreshold (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение свойства соединения **серверпрепаредстатементдискардсрешолд** . Этот параметр определяет, сколько невыполненных операций отмены подготовленной инструкции (sp_unprepare) может быть недоступно для каждого соединения, прежде чем будет выполнен вызов очистки необработанных дескрипторов на сервере. Если параметр имеет значение < = 1, действия при закрытии подготовленных инструкций выполняются немедленно. Если для этого параметра задано значение > 1, эти вызовы объединяются в пакеты, чтобы избежать издержек при слишком частом вызове sp_unprepare.

  
## <a name="syntax"></a>Синтаксис  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **целочисленное** значение свойства соединения **серверпрепаредстатементдискардсрешолд** .  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6,4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
