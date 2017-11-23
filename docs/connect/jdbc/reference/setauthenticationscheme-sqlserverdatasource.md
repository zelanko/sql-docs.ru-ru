---
title: "метода setAuthenticationScheme (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 769db93f9bc1e0609ebbebcadf2fdd6f3cda3b4c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setauthenticationscheme-sqlserverdatasource"></a>setAuthenticationScheme (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, какой тип встроенной безопасности должен использоваться приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
public void setAuthenticationScheme(String authenticationScheme);  
```  
  
#### <a name="parameters"></a>Параметры  
 *authenticationScheme*  
  
 Значения: **«JavaKerberos»** и значение по умолчанию **«NativeAuthentication»**. Дополнительные сведения см. в разделе [с помощью встроенной проверки подлинности Kerberos для подключения к SQL Server](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
