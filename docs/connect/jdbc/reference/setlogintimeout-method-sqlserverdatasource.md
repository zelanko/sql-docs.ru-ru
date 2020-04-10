---
title: Метод setLoginTimeout (SQLServerDataSource) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 83d6869075e296465ee9c60b0c5032407d4fe2da
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925755"
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
 Этот метод setLoginTimeout задается с помощью метода setLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
