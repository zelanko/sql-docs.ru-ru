---
title: "Метод setIntegratedSecurity (SQLServerDataSource) | Документы Microsoft"
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
apiname: SQLServerDataSource.setIntegratedSecurity
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c82fad6b2fe56afe748b22ea8c131e8aff0e25d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>Метод setIntegratedSecurity (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **логическое** значение, указывающее, включено ли свойство integratedSecurity.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>Параметры  
 *включить*  
  
 **значение true,** Если включено integratedSecurity. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Значение «**true**» для указания, что учетные данные Windows будет использоваться [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] для проверки подлинности пользователя или приложения. Если «**true**», [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] выполняет поиск в кэше учетных данных локального компьютера учетные данные, которые уже были предоставлены при входе в систему компьютера или сети. Если «**false**», необходимо указать имя пользователя и пароль.  
  
> [!NOTE]  
>  Это свойство поддерживается только на [!INCLUDE[msCoName](../../../includes/msconame_md.md)] операционных систем Windows.  
  
 Дополнительные сведения об использовании встроенной проверки подлинности см. в разделе [построения URL-АДРЕСЕ соединения](../../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
