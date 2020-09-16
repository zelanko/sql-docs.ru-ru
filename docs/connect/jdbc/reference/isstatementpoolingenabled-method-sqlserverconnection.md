---
description: Метод isStatementPoolingEnabled (SQLServerConnection)
title: Метод isStatementPoolingEnabled (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isStatementPoolingEnabled
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 76c6afdec909de1edce177e05599b37b4fa8c746
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433366"
---
# <a name="isstatementpoolingenabled-method-sqlserverconnection"></a>Метод isStatementPoolingEnabled (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает сведения о том, включено ли объединение инструкций в пул для этого подключения.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isStatementPoolingEnabled()  
```  

## <a name="return-value"></a>Возвращаемое значение
 **Логическое значение**, содержащее флаг, который указывает на то, включено ли создание пула инструкций.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
