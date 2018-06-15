---
title: setServerPreparedStatementDiscardThreshold метод (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a0105f615a123aa9ec4a4d329601c7992f76469
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845239"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold метод (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение свойства соединения serverPreparedStatementDiscardThreshold. Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр имеет значение < = 1 аннулирующие действия выполняются немедленно для подготовленной инструкции close. Если значение равно > 1 эти вызовы объединяются вместе, чтобы избежать слишком часто вызова sp_unprepare
 
## <a name="syntax"></a>Синтаксис  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Параметры  
 *serverPreparedStatementDiscardThreshold*  
  
 Новое значение **serverPreparedStatementDiscardThreshold** свойство соединения.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Замечания  
 Этот метод доступен из драйвера JDBC версии 6.4 и далее.
 
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
