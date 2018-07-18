---
title: Драйвер Microsoft ODBC для SQL Server в Windows | Документы Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5d818e4ce5c267432e6e456e11720f546ebaa19
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32856659"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Драйвер Microsoft ODBC для SQL Server в Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Драйверы Microsoft ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] — это изолированные драйверы ODBC, которые обеспечивают интерфейс программирования (API) реализация стандартные интерфейсы ODBC для Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Драйвер Microsoft ODBC для SQL Server можно использовать для создания новых приложений. Можно также обновить имеющиеся приложения в настоящее время использующие старый драйвер ODBC. Драйвер ODBC для SQL Server поддерживает подключения к базе данных SQL Azure, хранилище данных SQL Azure, 2017 г. SQL Server, SQL Server 2016, SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 и SQL Server 2005.  

## <a name="summary"></a>Сводка

| Версия       | Возможности, поддерживаемые      |
| ------------- |---------------| 
| 17 драйвера Microsoft ODBC для SQL Server | <ul><li>Всегда зашифровано поддержку BCP API</li><li>Новый атрибут строки подключения UseFMTONLY драйвер для использования устаревших метаданных в особых случаях, требующие временных таблиц</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Постоянное шифрование</li><li>Проверка подлинности Azure AD</li><li>Группы доступности AlwaysOn</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>Международное доменное имя (IDN)</li></ul> |
| Драйвер Microsoft ODBC 11 для SQL Server | <ul><li>Организация пулов соединений с учетом драйвера</li><li>Устойчивость подключений</li><li>Асинхронное выполнение (метод опроса)</li></ul> |    

## <a name="documentation"></a>Документация  
Эта документация для Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] включает в себя следующее:  
  
-   [Заметки о выпуске](../../../connect/odbc/windows/release-notes.md)  
-   [Функции Microsoft ODBC Driver for SQL Server в Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Системные требования, установка и файлы драйвера](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Организация пулов соединений с учетом драйвера в ODBC Driver для SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Образец асинхронного выполнения &#40;метод уведомления&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Устойчивость подключения в драйвере ODBC в Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Использование постоянного шифрования с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Использование Azure Active Directory с драйвером ODBC](../../../connect/odbc/using-azure-active-directory.md) 
-   [С помощью прозрачного сетевого разрешение IP-адресов](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Сообщество  
- [Блог команды разработчиков Microsoft ODBC Driver For SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Форум по доступу к данным SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>См. также  
- [Основные сведения об SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [SQL Server Native Client: вопросы и ответы](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [Справочник по программированию ODBC](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
