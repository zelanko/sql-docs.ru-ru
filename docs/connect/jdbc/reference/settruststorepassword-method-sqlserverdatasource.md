---
title: Метод setTrustStorePassword (SQLServerDataSource) | Документы Microsoft
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
- setTrustStorePassword Method (SQLServerDataSource)
apilocation:
- setTrustStorePassword Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: fa87cbde-71cc-4f21-bc07-f8ba2b6a0a3f
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dbd22d01c5c4523fdd04a12d68b9c716fd8643d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="settruststorepassword-method-sqlserverdatasource"></a>Метод setTrustStorePassword (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает пароль, используемый для проверки целостности данных trustStore.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setTrustStorePassword(java.lang.String trustStorePassword)  
```  
  
#### <a name="parameters"></a>Параметры  
 *trustStorePassword*  
  
 Объект **строка** , содержащее пароль, используемый для проверки целостности данных trustStore.  
  
## <a name="remarks"></a>Замечания  
 Свойство trustStorePassword можно указать вместе со свойством trustStore, и его значение используется для проверки целостности файла trustStore.  
  
 Если задано свойство trustStore, а свойство trustStorePassword не задано, проверка целостности trustStore не выполняется.  
  
 Если не задано ни одно из свойств trustStore и trustStorePassword, то драйвер будет использовать системные свойства виртуальной машины JAVA (JVM) — «javax.net.ssl.trustStore» и «javax.net.ssl.trustStorePassword». Если не задано значение системного свойства "javax.net.ssl.trustStorePassword", проверка целостности trustStore не выполняется.  
  
 Если свойство trustStore не задано, а свойство trustStorePassword задано, драйвер JDBC будет использовать файл, заданный "javax.net.ssl.trustStore" в качестве доверенного хранилища, целостность доверенного хранилища проверяется с использованием указанного trustStorePassword. Это может потребоваться в случае, если клиентское приложение не желает сохранять пароль с системном свойстве JVM.  
  
 Дополнительные сведения см. в разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Начиная с версии 3.0 драйвера JDBC, если SQLServerDataSource.setTrustStorePassword задается до привязки свойств источника данных, необходимо вызвать метод SQLServerDataSource.setTrustStorePassword перед получением соединения. Дополнительные сведения см. в разделе [SQLServerDataSource.getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
