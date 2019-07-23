---
title: Метод setServerPreparedStatementDiscardThreshold (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: 28c3a442f89813a4ce93ded9035c1bc16f9e47c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972841"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>Метод setServerPreparedStatementDiscardThreshold (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение свойства соединения Серверпрепаредстатементдискардсрешолд. Этот параметр определяет, сколько невыполненных операций отмены подготовленной инструкции (sp_unprepare) может быть недоступно для каждого соединения, прежде чем будет выполнен вызов очистки необработанных дескрипторов на сервере. Если параметр имеет значение < = 1, действия при закрытии подготовленных инструкций выполняются немедленно. Если значение равно > 1, эти вызовы объединяются в пакеты, чтобы избежать чрезмерных затрат на вызов sp_unprepare слишком часто
 
## <a name="syntax"></a>Синтаксис  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Параметры  
 *серверпрепаредстатементдискардсрешолд*  
  
 Новое значение свойства соединения **серверпрепаредстатементдискардсрешолд** .  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен из драйвера JDBC версии 6,4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
