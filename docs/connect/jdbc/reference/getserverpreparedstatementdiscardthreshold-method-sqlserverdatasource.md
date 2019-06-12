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
manager: jroth
ms.openlocfilehash: 13c2512b3d66a324947c73c7d5030c03a1e9294e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66791884"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>Метод getServerPreparedStatementDiscardThreshold (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение **параметр serverPreparedStatementDiscardThreshold** свойство соединения. Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр установлен в < = 1 unprepare действия выполняются немедленно для подготовленной инструкции close. Если это значение > 1 эти вызовы будут объединены в один пакет во избежание издержки вызове процедура sp_unprepare слишком часто.

  
## <a name="syntax"></a>Синтаксис  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **int** значение **параметр serverPreparedStatementDiscardThreshold** свойство соединения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
