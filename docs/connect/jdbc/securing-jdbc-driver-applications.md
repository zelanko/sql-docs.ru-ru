---
title: "Защита приложений драйвера JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8033e1690fcaa01ca73ce1a7d0d9972ac2d3ba9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="securing-jdbc-driver-applications"></a>Защита приложений драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Повышение безопасности [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] приложения предполагает не только избежание типичных ошибок в коде. В приложении, имеющем доступ к данным, существует много потенциальных точек сбоя, которые злоумышленник может использовать для извлечения, манипуляции или разрушения конфиденциальных данных. Важно понимать все аспекты безопасности от процесса моделирования угрозы на этапе разработки приложения до момента развертывания и далее на всем протяжении его использования.  
  
 В подразделах данного раздела приводится описание некоторых общих вопросов безопасности, включая строки соединения, проверку вводимых пользователем данных и общую безопасность приложения.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Защита строк подключения](../../connect/jdbc/securing-connection-strings.md)|Описывает техники защиты информации, используемые для подключения к источнику данных.|  
|[Проверка пользовательского ввода](../../connect/jdbc/validating-user-input.md)|Описывает техники проверки вводимых пользователем данных.|  
|[Безопасность приложений](../../connect/jdbc/application-security.md)|Описывает использование разрешений политики Java для обеспечения безопасности приложения драйвера JDBC.|  
|[С помощью шифрования SSL](../../connect/jdbc/using-ssl-encryption.md)|Описывает установление безопасного канала связи с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью Secure Sockets Layer (SSL).|  
|[Режим FIPS](../../connect/jdbc/fips-mode.md)|Описывает способы использования драйвера JDBC в режиме FIPS complainant.| 
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
