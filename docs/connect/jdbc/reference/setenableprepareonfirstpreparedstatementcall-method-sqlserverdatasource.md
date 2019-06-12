---
title: Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: 18cd626fb3eee4690d87dd40edd50e64a4dcd98e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779136"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>Метод setEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает поведение для определенного подключения экземпляра. Если эта конфигурация имеет значение false, вызывает sp_executesql и не Подготовка инструкции, после второго выполнения он будет вызывать sp_prepexec и фактически установки дескриптором подготовленной инструкции первого выполнения подготовленной инструкции. После выполнения вызовет sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз.  
## <a name="syntax"></a>Синтаксис  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Параметры  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Новое значение **enablePrepareOnFirstPreparedStatementCall** свойство соединения.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
