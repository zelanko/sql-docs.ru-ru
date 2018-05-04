---
title: Метод setHostNameInCertificate (SQLServerDataSource) | Документы Microsoft
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
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aae071ffe1c3bee7017dfdf46440829d231207f4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>Метод setHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя узла, используемого для проверки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] сертификат Secure Sockets Layer (SSL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Параметры  
 *hostNameInCertificate*  
  
 Объект **строка** , содержащее имя узла.  
  
## <a name="remarks"></a>Замечания  
 Значение hostNameInCertificate используется для проверки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] сертификата SSL, если уровень связи шифруется с помощью протокола SSL. По умолчанию используется значение NULL.  
  
 Если свойство hostNameInCertificate имеет значение null или определен, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] использует значение свойства serverName для проверки соответствия [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL-сертификат. Если для свойства hostNameInCertificate задано строковое значение или пустая строка "", драйвер использует это значение для проверки SSL-сертификата сервера.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
