---
title: Метод setLoginTimeout (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b655449b2b15e7fbf1f31f7045bc5f0051951a2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681122"
---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Метод setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает время ожидания в секундах для объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) при попытке установить соединение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Параметры  
 *loginTimeout*  
  
 Значение **int**, представляющее число секунд ожидания. Нулевое значение означает, что время ожидания равно системному времени ожидания по умолчанию, т.е. 15 секундам.  
  
## <a name="remarks"></a>Remarks  
 Этот метод setLoginTimeout указывается с помощью метода setLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
