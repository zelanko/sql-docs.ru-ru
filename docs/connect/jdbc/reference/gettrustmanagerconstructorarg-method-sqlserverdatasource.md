---
title: Метод getTrustManagerConstructorArg (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerConstructorArg
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f3af347e41f3ba90b283b56d8cb2c1550b69006
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978592"
---
# <a name="gettrustmanagerconstructorarg-method-sqlserverdatasource"></a>Метод getTrustManagerConstructorArg (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает строковое значение свойства подключения TrustManagerConstructorArg.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getTrustManagerConstructorArg()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение свойства подключения TrustManagerConstructorArg или NULL, если это свойство не имеет значения.  
  
## <a name="remarks"></a>Remarks  
 Если свойство TrustManagerClass не задано, то метод [getTrustManagerConstructorArg](../../../connect/jdbc/reference/gettrustmanagerconstructorarg-method-sqlserverdatasource.md) возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
