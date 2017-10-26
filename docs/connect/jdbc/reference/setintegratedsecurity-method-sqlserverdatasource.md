---
title: "Метод setIntegratedSecurity (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b0480212d2216f66d917debcd7565093d89c9d78
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
  

