---
description: Метод getTrustManagerConstructorArg (SQLServerDataSource)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: edda767e361b540833babd0125f3f13ad5f2fb08
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433976"
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
  
  
