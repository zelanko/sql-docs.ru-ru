---
title: "Функции Microsoft ODBC Driver for SQL Server в Windows | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3916b53dcccf77cea96b5d12ce61273569b33dc3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Функции Microsoft ODBC Driver for SQL Server в Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Microsoft ODBC Driver 13.1 for SQL Server в Windows

ODBC Driver 13.1 for SQL Server содержит все функциональные возможности предыдущей версии (11), а также добавляет поддержку проверки подлинности постоянного шифрования и Azure Active Directory при использовании в сочетании с Microsoft SQL Server 2016.  
  
Функция Always Encrypted позволяет клиентам шифровать конфиденциальные данные в клиентских приложениях, не раскрывая ключи шифрования для SQL Server. Драйвер с поддержкой Always Encrypted, установленный на клиентском компьютере, реализует это за счет автоматического шифрования и расшифровки конфиденциальных данных в клиентском приложении SQL Server. Драйвер шифрует данные из конфиденциальных столбцов перед их передачей в SQL Server и автоматически переписывает запросы, чтобы сохранить семантику приложения. Аналогичным образом драйвер прозрачно расшифровывает данные, хранящиеся в столбцах зашифрованной базы данных, которые содержатся в результатах запроса. Дополнительные сведения см. в разделе [использование постоянного шифрования с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Позволяет Azure Active Directory пользователей, Администраторов и разработчики приложений для использования проверки подлинности Azure Active Directory в качестве механизма подключения к базе данных SQL Microsoft Azure и Microsoft SQL Server 2016 с помощью удостоверений в Azure Active Directory (Azure AD ). Дополнительные сведения см. в разделе [с помощью Azure Active Directory с помощью драйвера ODBC](../../../connect/odbc/using-azure-active-directory.md), и [подключение к базе данных SQL или SQL данные хранилища с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Драйвер Microsoft ODBC 11 для SQL Server в Windows  

Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] содержит все функциональные возможности драйвера ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client, который входит в состав [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. Дополнительные сведения см. в статье [Программирование SQL Server Native Client](http://msdn.microsoft.com/library/ms130892.aspx). Драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client основан на драйвере ODBC, который входит в состав операционной системы Windows. Дополнительные сведения см. в статье [Пакет SDK компонентов доступа к данным Windows DAC](http://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
Этот выпуск драйвера ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] содержит следующие новые функции:  
  
### <a name="bcpexe-l-option-for-specifying-a-login-timeout"></a>параметр – l bcp.exe для указания время ожидания входа
 
Параметр – l задает количество секунд до `bcp.exe` входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] время ожидания при попытке подключения к серверу. По умолчанию время ожидания входа составляет 15 секунд. Время ожидания входа должно быть числом от 0 до 65534. Если указанное значение не является числом или выходит за пределы указанного диапазона, программа `bcp.exe` выдает сообщение об ошибке. Значение 0 задает неограниченное время ожидания. Время ожидания входа менее (приблизительно) 10 секунд, не является надежным.  
  
### <a name="driver-aware-connection-pooling"></a>Организация пулов соединений с учетом драйвера  
Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддерживает [Driver-Aware Connection Pooling](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). Дополнительные сведения см. в статье [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Асинхронное выполнение (метод уведомления)  
Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддерживает [асинхронное выполнение (метод уведомления)](http://msdn.microsoft.com/library/hh405038(VS.85).aspx). Пример использования см. в разделе [асинхронного выполнения &#40; Метод уведомления &#41; Образец](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Устойчивость подключений
Чтобы обеспечить сохранение подключения приложений к Базе данных SQL Microsoft Azure, драйвер ODBC в Windows может восстанавливать неактивные соединения. Дополнительные сведения см. в статье [Connection Resiliency in the Windows ODBC Driver](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Изменения в работе

В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client `-y0` для параметра `sqlcmd.exe` приводит к усечено до 1 МБ, если ширина экрана было равно 0.
  
Начиная с ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], нет ограничений на объем данных, которые можно получить в одном столбце при `–y0` указано. `sqlcmd.exe`Теперь потоковую передачу столбцов размером до 2 ГБ ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] максимальное значение для типа данных).  
  
Другое отличие состоит в том, что указание оба `-h` и `-y0` теперь приводит к ошибке, сообщение о том, что эти параметры несовместимы. `-h`, который указывает количество строк для печати между заголовками столбцов и не был совместим с `-y0`, было пропущено, хотя заголовки не выводились.
  
Обратите внимание, что `-y0` может вызвать проблемы с производительностью на сервере и сети, в зависимости от размера возвращаемых данных.

## <a name="see-also"></a>См. также:  
[Драйвер Microsoft ODBC для SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  

