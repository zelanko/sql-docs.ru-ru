---
title: "Метод setTrustServerCertificate (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 48b6e5131a81cf79a3eddf110c20a3340cbb48d7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Метод setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **логическое** значение, указывающее, включено ли свойство trustServerCertificate.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Параметры  
 *trustServerCertificate*  
  
 **значение true,** при сертификат Secure Sockets Layer (SSL) сервера должен быть автоматически считаться доверенным, когда на уровне связи применяется шифрование SSL. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство trustServerCertificate имеет значение **true**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL-сертификат автоматически считается доверенным, когда на уровне связи применяется шифрование SSL. Другими словами [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не будет проверять [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL-сертификат. Значение по умолчанию — **false**.  
  
 Если свойство trustServerCertificate имеет значение **false**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет проверять SSL-сертификата сервера.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

