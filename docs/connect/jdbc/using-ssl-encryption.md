---
title: "С помощью шифрования SSL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7923995b392dff8c80f1ee6ae3946e421dc46331
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-ssl-encryption"></a>Использование SSL-шифрования
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Безопасное шифрование Sockets Layer (SSL) поддерживает передачу зашифрованных данных по сети между экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и клиентским приложением.  
  
 Шифрование SSL ― это протокол для установления безопасного канала связи и предотвращения перехвата критических или конфиденциальных сведений в сети и по другим каналам связи. Шифрование SSL позволяет клиенту и серверу выполнить взаимную проверку подлинности. После проверки подлинности шифрование SSL обеспечивает зашифрованное соединение между участниками канала для безопасной передачи сообщений.  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Обеспечивает инфраструктуру включения и выключения шифрования для определенного соединения, в зависимости от пользователя, указанного свойства соединения и параметров сервера и клиента. Пользователь может указать место хранения сертификата и пароль, имя узла, используемого для проверки сертификата, а также когда следует шифровать канал.  
  
 Шифрование SSL повышает защищенность обмена данными по сети между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и приложениями. Включение шифрования не снижает производительности.  
  
 В этом разделе описываются как [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] версия поддерживает SSL-шифрование, включая новые свойства соединения и настройка доверенного хранилища на стороне клиента.  
  
> [!NOTE]  
>  **HostNameInCertificate** рекомендуется использовать свойство для проверки SSL-сертификат.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основные сведения о поддержке SSL](../../connect/jdbc/understanding-ssl-support.md)|Описывает способ [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает SSL-шифрование.|  
|[Подключение с шифрованием SSL](../../connect/jdbc/connecting-with-ssl-encryption.md)|Описывает, как подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью новых свойств подключения SSL.|  
|[Настройка клиента для SSL-шифрования](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)|Описывает настройку доверенного хранилища по умолчанию на стороне клиента и импорт личного сертификата в доверенное хранилище клиентского компьютера.|  
  
## <a name="see-also"></a>См. также:  
 [Защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

