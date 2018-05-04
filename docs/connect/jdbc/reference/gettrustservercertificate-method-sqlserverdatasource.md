---
title: Метод getTrustServerCertificate (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 159b87346779aa2dda46249dcd808266d95b69df
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>Метод getTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включено ли свойство trustServerCertificate.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если включен trustServerCertificate. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство trustServerCertificate имеет значение **true**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Secure Sockets Layer (SSL) сертификат автоматически считается доверенным, когда на уровне связи применяется шифрование SSL. Другими словами [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не будет проверять [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL-сертификат. Значение по умолчанию — **false**.  
  
 Если свойство trustServerCertificate имеет значение **false**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет проверять SSL-сертификата сервера.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
