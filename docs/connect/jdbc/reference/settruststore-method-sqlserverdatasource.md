---
title: Метод setTrustStore (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf5d6034fbf2e9ce9d1c1b58909146dbcf56f0c6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042284"
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
  
-   2. "\<java-home >/lib/security/jssecacerts» файл.  
  
-   3. "\<java-home >/lib/security/cacerts» файл.  
  
 Дополнительные сведения см. в документации интерфейса SunX509 TrustManager на веб-сайте компании Sun Microsystems.  
  
 Если для свойства trustStore задано строковое значение или пустая строка "", то драйвер воспользуется этим значением, чтобы найти файл trustStore для проверки SSL-сертификата сервера.  
  
 Свойство trustStorePassword можно указать вместе со свойством trustStore, и его значение используется для открытия файла trustStore. Дополнительные сведения см. в разделе [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
