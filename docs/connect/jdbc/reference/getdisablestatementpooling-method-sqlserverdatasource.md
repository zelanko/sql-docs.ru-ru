---
description: Метод getDisableStatementPooling (SQLServerDataSource)
title: Метод getDisableStatementPooling (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: 902cceb335ea1f4f5a5858ae3bc80354002ba77b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436226"
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>Метод getDisableStatementPooling (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение свойства **disableStatementPooling** для подключения. Этот параметр определяет, включено ли объединение инструкций в пул для этого подключения.

  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Логическое** значение, которое содержит свойство подключения **disableStatementPooling**.
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
