---
title: Метод getTrustManagerClass (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getTrustManagerClass
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 327dcad497c934c787d509a41f0068691bf5588a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786223"
---
# <a name="gettrustmanagerclass-method-sqlserverdatasource"></a>Метод getTrustManagerClass (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает строковое значение свойства соединения TrustManagerClass.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getTrustManagerClass()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий значение свойства соединения TrustManagerClass, или значение null, если значение не задано.  
  
## <a name="remarks"></a>Remarks  
 Если не задано свойство TrustManagerClass, [getTrustManagerClass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md) метод возвращает значение null.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
