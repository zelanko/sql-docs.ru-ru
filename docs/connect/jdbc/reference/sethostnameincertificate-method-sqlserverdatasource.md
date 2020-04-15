---
title: Метод setHostNameInCertificate (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 418e9aea8d44d3be23bc21c5a8950c5788e7c07a
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219304"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>Метод setHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя узла, используемого для проверки TLS-сертификата [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который ранее назывался SSL-сертификатом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Параметры  
 *hostNameInCertificate*  
  
 Значение типа **String**, содержащее имя узла.  
  
## <a name="remarks"></a>Remarks  
 Значение hostNameInCertificate используется для проверки TLS/SSL-сертификата [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при использовании шифрования TLS для уровня связи. По умолчанию используется значение NULL.  
  
 Если свойство hostNameInCertificate имеет значение NULL или оно не указано, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] использует значение свойства serverName для проверки по TLS/SSL-сертификату [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если для свойства hostNameInCertificate задано строковое значение или пустая строка "", драйвер использует это значение для проверки TLS/SSL-сертификата сервера.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
