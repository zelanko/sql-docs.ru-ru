---
title: Microsoft ODBC Driver for SQL Server в Windows | Документы Майкрософт
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c075c7adcc7eeae3ae7a83676256e72b4b86d187
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989428"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Драйвер Microsoft ODBC для SQL Server в Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Драйверы Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] — это автономные драйверы ODBC, предоставляющие программный интерфейс (API), который реализует стандартные интерфейсы ODBC для Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Microsoft ODBC Driver for SQL Server можно использовать для создания приложений. Можно также обновить имеющиеся приложения, использующие старый драйвер ODBC. Драйвер ODBC Driver for SQL Server поддерживает подключения к базе данных SQL Azure, хранилищу данных SQL Azure, SQL Server 2017, SQL Server 2016, SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 и SQL Server 2005.  

## <a name="summary"></a>Сводка

| Версия       | Поддерживаемые возможности      |
| ------------- |---------------| 
| Microsoft ODBC Driver for SQL Server версии 17 | <ul><li>Поддержка Always Encrypted для API BCP</li><li>Новый атрибут строки подключения UseFMTONLY предписывает драйверу использовать старые метаданные в особых случаях, в которых требуются временные таблицы</li>
| Microsoft ODBC Driver for SQL Server версии 13.1     | <ul><li>Always Encrypted</li><li>Аутентификация Azure AD</li><li>Группы доступности AlwaysOn</li></ul>   | 
| Microsoft ODBC Driver for SQL Server версии 13      | <ul><li>Международное доменное имя (IDN)</li></ul> |
| Драйвер Microsoft ODBC 11 для SQL Server | <ul><li>Организация пулов соединений с учетом драйвера</li><li>Устойчивость подключений</li><li>Асинхронное выполнение (метод опроса)</li></ul> |    

## <a name="documentation"></a>Документация  
Эта документация для Microsoft ODBC Driver для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включает в себя следующее:  
  
-   [Заметки о выпуске ODBC для SQL Server в Windows](../../../connect/odbc/windows/release-notes-odbc-sql-server-windows.md)  
-   [Функции Microsoft ODBC Driver for SQL Server в Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Системные требования, установка и файлы драйвера](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Организация пулов соединений с учетом драйвера в ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Образец асинхронного выполнения &#40;метод уведомления&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Устойчивость подключения в драйвере ODBC в Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Использование функции Always Encrypted с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Использование Azure Active Directory с драйвером ODBC](../../../connect/odbc/using-azure-active-directory.md) 
-   [Использование разрешения IP-адресов прозрачной сети](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Сообщество  
- [Блог команды разработчиков Microsoft ODBC Driver For SQL Server](https://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Форум по доступу к данным SQL Server](https://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>См. также:  
- [Основные сведения об SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Построение приложений с использованием SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [SQL Server Native Client: вопросы и ответы](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [Справочник по программированию ODBC](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
