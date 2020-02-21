---
title: Метод setStatementPoolingCacheSize (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setStatementPoolingCacheSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d8f4ad3463cce03e9c83c936d028e480aef52dd9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972785"
---
# <a name="setstatementpoolingcachesize-method-sqlserverconnection"></a>Метод setStatementPoolingCacheSize (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Задает размер кэша подготовленных инструкций для этого подключения. Кэш используется, если disableStatementPooling имеет значение false, а этому параметру присвоено значение больше 0.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setStatementPoolingCacheSize(int statementPoolingCacheSize)  
```  

#### <a name="parameters"></a>Параметры  
 *statementPoolingCacheSize*  
  
 Новое значение для свойства подключения **statementPoolingCacheSize**.  

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC версии 6.4 или более поздней.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
