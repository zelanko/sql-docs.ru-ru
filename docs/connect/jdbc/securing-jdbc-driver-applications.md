---
title: Защита приложений драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11330ade60084a5e3995b5acf565d26f3b4da62b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979216"
---
# <a name="securing-jdbc-driver-applications"></a>Защита приложений драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Повышение уровня безопасности приложения [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предполагает не только избежание типичных ошибок в коде. В приложении, имеющем доступ к данным, существует много потенциальных точек сбоя, которые злоумышленник может использовать для извлечения, манипуляции или разрушения конфиденциальных данных. Важно понимать все аспекты безопасности от процесса моделирования угрозы на этапе разработки приложения до момента развертывания и далее на всем протяжении его использования.  
  
 В подразделах данного раздела приводится описание некоторых общих вопросов безопасности, включая строки соединения, проверку вводимых пользователем данных и общую безопасность приложения.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Обеспечение безопасности строк подключений](../../connect/jdbc/securing-connection-strings.md)|Описывает техники защиты информации, используемые для подключения к источнику данных.|  
|[Проверка вводимых пользователем данных](../../connect/jdbc/validating-user-input.md)|Описывает техники проверки вводимых пользователем данных.|  
|[Безопасность приложений](../../connect/jdbc/application-security.md)|Описывает использование разрешений политики Java для обеспечения безопасности приложения драйвера JDBC.|  
|[Использование SSL-шифрования](../../connect/jdbc/using-ssl-encryption.md)|Описывает установление безопасного соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с использованием SSL-шифрования.|  
|[Режим FIPS](../../connect/jdbc/fips-mode.md)|Описывает способы использования драйвера JDBC в режиме совместимости с FIPS.| 
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
