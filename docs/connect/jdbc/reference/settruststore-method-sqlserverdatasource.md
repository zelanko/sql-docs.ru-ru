---
title: Метод setTrustStore (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be54aea70e712d2209c04196d3e450bca488578b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67972193"
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
  
 Объект типа **String**, который содержит путь к файлу trustStore сертификата (включая имя файла).  
  
## <a name="remarks"></a>Remarks  
 Если свойство trustStore не задано или имеет значение NULL, то драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет использовать правила поиска фабрики диспетчеров доверия, чтобы определить, какое хранилище сертификатов следует использовать. Используемая по умолчанию фабрика SunX509 TrustManagerFactory пытается найти материал доверия в следующих местах в следующем порядке:  
  
-   1. Файл, указанный системным свойством javax.net.ssl.trustStore виртуальной машины Java (JVM).  
  
-   2. Файл \<java-home>/lib/security/jssecacerts.  
  
-   3. Файл \<java-home>/lib/security/cacerts.  
  
 Дополнительные сведения см. в документации интерфейса SunX509 TrustManager на веб-сайте компании Sun Microsystems.  
  
 Если для свойства trustStore задано строковое значение или пустая строка "", то драйвер воспользуется этим значением, чтобы найти файл trustStore для проверки SSL-сертификата сервера.  
  
 Свойство trustStorePassword можно указать вместе со свойством trustStore, и его значение используется для открытия файла trustStore. Дополнительные сведения см. в разделе [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
