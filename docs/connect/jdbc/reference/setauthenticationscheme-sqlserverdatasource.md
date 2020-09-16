---
description: setAuthenticationScheme (SQLServerDataSource)
title: setAuthenticationScheme (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b942f78e-7ce1-44ef-923d-a7c3d7c76b83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce58c0a0bef0814e4128f8e540f8d8f92251e3e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432546"
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
  
 Используются значение **JavaKerberos** и значение по умолчанию **NativeAuthentication**. Дополнительные сведения см. в статье [Использовании встроенной проверки подлинности Kerberos для подключения к SQL Server](../../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
