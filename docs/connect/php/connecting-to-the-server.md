---
title: "Подключение к серверу | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c251a239-e0bd-4f45-9207-b76651072dd0
caps.latest.revision: 44
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d314d1da7a072fc6b2b95dc54acf66ce07a3676e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-to-the-server"></a>Подключение к серверу
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Статьи, приведенные в этом разделе, описывают параметры и процедуры для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] может подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с использованием проверки подлинности Windows или проверки подлинности SQL Server. По умолчанию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] пытаются подключиться к серверу с использованием проверки подлинности Windows.  

## <a name="in-this-section"></a>В этом разделе  

|Раздел|Описание|  
|---------|---------------|  
|[Практическое руководство. Подключение с использованием проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md)|Описывает, как установить соединение с использованием проверки подлинности Windows.|  
|[Практическое руководство. Подключение с использованием проверки подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)|Описывает, как установить соединение с использованием проверки подлинности SQL Server.|  
|[Практическое руководство. Подключение с использованием проверки подлинности Azure Active Directory](../../connect/php/azure-active-directory.md)|Описывает, как задать режим проверки подлинности и подключение с использованием удостоверения Azure Active Directory.|  
|[Практическое руководство. Подключение к заданному порту](../../connect/php/how-to-connect-on-a-specified-port.md)|Описывает, как подключиться к серверу через определенный порт.|  
|[Организация пулов соединений](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)|Предоставляет сведения об использовании пулов подключений в драйвере.|  
|[Практическое руководство. Отключение множественных активных результирующих наборов (функция MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)|Описывает отключение функции MARS при установке соединения.|  
|[Параметры соединения](../../connect/php/connection-options.md)|Содержит список параметров, которые допускаются в ассоциативном массиве, содержащем атрибуты подключения.|  
|[PHP Driver for SQL Server Support for LocalDB (Поддержка драйвера PHP для SQL Server для LocalDB)](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)|Описывает поддержку [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] функции LocalDB, которая была добавлена в [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)].|  
|[Поддержка драйвера PHP для SQL Server для функций высокого уровня доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)|Описывает, как можно настроить приложение, чтобы воспользоваться преимуществами высокого уровня доступности, аварийного восстановления, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)].|  
|[Подключение к базе данных Microsoft Azure SQL](../../connect/php/connecting-to-microsoft-azure-sql-database.md)|Описывает соединение с базой данных SQL Azure.|  
|[Устойчивость подключений](../../connect/php/connection-resiliency.md)|Обсуждается функция устойчивости подключений восстанавливающей прерванных соединений.|  

## <a name="see-also"></a>См. также:  
[Руководство по программированию для драйвера PHP SQL](../../connect/php/programming-guide-for-php-sql-driver.md)
[пример приложения &#40; Драйвер SQLSRV &#41;](../../connect/php/example-application-sqlsrv-driver.md)  

