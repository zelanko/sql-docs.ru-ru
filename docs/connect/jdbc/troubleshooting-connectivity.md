---
title: "Устранение неполадок с подключением | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4adcdafe8b82a8b35dbb9b27c15749673a56bce2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="troubleshooting-connectivity"></a>Устранение неполадок подключения
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Необходим TCP/IP установлена и запущена для взаимодействия с вашей [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Configuration Manager установленные протоколы сетевой библиотеки.  
  
 Попытка подключить к базе данных может завершиться с ошибкой по многим причинам. Можно выполнить следующие действия.  
  
-   Протокол TCP/IP не включен для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], или сервер или номер порта указан неверно. Убедитесь, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с TCP/IP прослушивает указанный порт на указанном сервере. При этом может быть вызвано исключение, схожее с «Не удалось войти в систему. Не удалось соединиться с узлом по протоколу TCP/IP". Это указывает на одну из следующих причин:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]установлен, но не был установлен сетевой протокол для TCP/IP [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Network Utility для [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Configuration Manager для [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] и более поздних версий.  
  
    -   TCP/IP установлен в качестве [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] протокола, но он не прослушивает порт, указанный в URL-АДРЕСЕ соединения JDBC. По умолчанию используется порт 1433, но [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] можно настроить при установке продукта прослушивание любого порта. Убедитесь, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] прослушивает порт 1433. Кроме того, если порт был изменен, убедитесь, что порт, указанный в URL-адресе для соединения с JDBC, совпадает с измененным портом. Дополнительные сведения о URL-адреса подключения JDBC см. в разделе [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md).  
  
    -   Адрес компьютера, указанное в соединении JDBC URL-адрес не ссылается на сервер где [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] будет установлена и запущена.  
  
    -   Протоколу TCP/IP между клиентом и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] нарушено взаимодействие. Проверьте подключение TCP/IP к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , с помощью программы telnet. Например, в командной строке введите `telnet 192.168.0.0 1433` где 192.168.0.0 — это адрес компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , который он прослушивает порт 1433. Если появится сообщение о том, «Подключение Telnet невозможно», TCP/IP не прослушивает этот порт для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключений. Используйте [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Network Utility для [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Configuration Manager для [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] и более поздней версии, чтобы убедиться, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] настроен на использование TCP/IP по порту 1433.  
  
    -   Используемый сервером порт закрыт брандмауэром. Это может быть порт, используемый сервером, или (необязательно) порт, связанный с именованным экземпляром сервера.  
  
-   Указано неверное имя базы данных. Убедитесь, что осуществляется вход в существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.  
  
-   Неправильное имя пользователя или пароль. Проверьте вводимые данные.  
  
-   При использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, драйвер JDBC требует, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] устанавливается вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, который не используется по умолчанию. Убедитесь, что этот параметр включен, при установке или настройке вашего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)   
 [Подключение к SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

