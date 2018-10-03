---
title: Метод getStatementPoolingCacheSize (SQLServerDataSource) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 9b73cd6a660d5e03702a7b7aa2ed58d0e7817d6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837992"
---
# <a name="getstatementpoolingcachesize-method-sqlserverdatasource"></a>Метод getStatementPoolingCacheSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение **значение параметра statementPoolingCacheSize** свойство соединения. Возвращает размер кэша подготовленных инструкций для этого подключения. "0" означает, что не включено кэширование.
  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getStatementPoolingCacheSize();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение **значение параметра statementPoolingCacheSize** свойство соединения.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод, доступные в версии драйвера JDBC 6.4 и далее.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
