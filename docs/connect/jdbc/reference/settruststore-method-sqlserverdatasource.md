---
title: "Метод setTrustStore (SQLServerDataSource) | Документы Microsoft"
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
apiname: setTrustStore Method (SQLServerDataSource)
apilocation: setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40cd49482379490d3ac80570bde16ce7f8a81253
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="settruststore-method-sqlserverdatasource"></a>Метод setTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает путь к файлу сертификата trustStore (включая имя файла).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>Параметры  
 *trustStore*  
  
 Объект **строка** , содержащее путь (включая имя файла) к файлу сертификата trustStore.  
  
## <a name="remarks"></a>Замечания  
 Если свойство trustStore не задано или задано значение null, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет зависеть от правила, чтобы определить, какое хранилище сертификатов следует использовать поиска фабрики диспетчеров доверия. Используемая по умолчанию фабрика SunX509 TrustManagerFactory пытается найти материал доверия в следующих местах в следующем порядке:  
  
-   1. Файл, указанный системным свойством javax.net.ssl.trustStore виртуальной машины Java (JVM).  
  
-   2. «\<java-home >/lib/безопасность/jssecacerts» файла.  
  
-   3. «\<java-home >/lib/безопасность/cacerts» файла.  
  
 Дополнительные сведения см. в документации интерфейса SunX509 TrustManager на веб-сайте компании Sun Microsystems.  
  
 Если для свойства trustStore задано строковое значение или пустая строка "", то драйвер воспользуется этим значением, чтобы найти файл trustStore для проверки SSL-сертификата сервера.  
  
 Свойство trustStorePassword можно указать вместе со свойством trustStore, и его значение используется для открытия файла trustStore. Дополнительные сведения см. в разделе [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
