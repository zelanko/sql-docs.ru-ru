---
description: Использование шифрования
title: Использование шифрования
ms.custom: Learn how to establish secure communication channels using TLS encryption with your SQL database connections.
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: vanto
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86a36cec5930630c00501796e9c2340106cfa6c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414580"
---
# <a name="using-encryption"></a>Использование шифрования

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

TLS-шифрование позволяет передавать по сети зашифрованные данные между экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и клиентским приложением.  
  
Шифрование TLS ― это протокол для установления безопасного канала связи и предотвращения перехвата критических или конфиденциальных сведений в сети и по другим каналам связи. Шифрование TLS позволяет клиенту и серверу выполнить взаимную проверку подлинности. После проверки подлинности шифрование TLS обеспечивает зашифрованное соединение между участниками канала для безопасной передачи сообщений.  
  
Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] обеспечивает инфраструктуру для активации и деактивации шифрования на определенных подключениях в зависимости от заданных пользователям свойств, а также параметров сервера и клиента. Пользователь может указать место хранения сертификата и пароль, имя узла, используемого для проверки сертификата, а также когда следует шифровать канал.  
  
Шифрование TLS повышает защищенность обмена данными по сети между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и приложениями. Включение шифрования не снижает производительности.  
  
В разделах этой статьи описана реализация TLS-шифрования в версии драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], в том числе новые свойства подключений, а также процедура настройки доверенного хранилища на стороне клиента.  
  
> [!NOTE]  
> Рекомендуется использовать свойство подключения **hostNameInCertificate** для проверки сертификата TLS.  

## <a name="in-this-section"></a>В этом разделе  

| Раздел                                                                                                        | Description                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Основные сведения о поддержке шифрования](../../connect/jdbc/understanding-ssl-support.md)                                 | Описание поддержки TLS-шифрования в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].                                              |
| [Подключение с шифрованием](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | Описание подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием новых свойств соединения, относящихся к TLS. |
| [Настройка шифрования на клиенте](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | Описывает настройку доверенного хранилища по умолчанию на стороне клиента и импорт личного сертификата в доверенное хранилище клиентского компьютера.   |
  
## <a name="see-also"></a>См. также раздел

[Защита приложений JDBC Driver](../../connect/jdbc/securing-jdbc-driver-applications.md)  
