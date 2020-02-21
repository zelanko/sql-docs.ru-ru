---
title: Метод getDisableStatementPooling (SQLServerDataSource) | Документация Майкрософт
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
ms.openlocfilehash: 108bc70b3ff4a3fb03d332def79f9ceebeffd94a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983645"
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>Метод getDisableStatementPooling (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение свойства подключения **disableStatementPooling**. Этот параметр определяет, включено ли создание пула инструкций для этого подключения.

  
## <a name="syntax"></a>Синтаксис  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Логическое** значение, которое содержит свойство подключения **disableStatementPooling**.
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC версии 6.4 или более поздней.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
