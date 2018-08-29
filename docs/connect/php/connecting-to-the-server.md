---
title: Подключение к SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c251a239-e0bd-4f45-9207-b76651072dd0
caps.latest.revision: 44
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36a147c4231d9c2c90f0f2151d4e69bebd5eefb1
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785850"
---
# <a name="connecting-to-the-server"></a>Подключение к серверу
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Статьи, приведенные в этом разделе, описывают параметры и процедуры для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] может подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows или проверки подлинности SQL Server. По умолчанию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] пытаются подключиться к серверу с использованием проверки подлинности Windows.  

## <a name="in-this-section"></a>в этом разделе  

|Раздел|Описание|  
|---------|---------------|  
|[Практическое руководство. Подключение с использованием проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md)|Описывает, как установить соединение с использованием проверки подлинности Windows.|  
|[Практическое руководство. Подключение с использованием проверки подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)|Описывает, как установить соединение с использованием проверки подлинности SQL Server.|  
|[Практическое руководство. Подключение с использованием проверки подлинности Azure Active Directory](../../connect/php/azure-active-directory.md)|Описывает, как установить режим проверки подлинности и подключиться с помощью удостоверения Azure Active Directory.|  
|[Практическое руководство. Подключение к заданному порту](../../connect/php/how-to-connect-on-a-specified-port.md)|Описывает, как подключиться к серверу через определенный порт.|  
|[Организация пулов соединений](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)|Предоставляет сведения об использовании пулов подключений в драйвере.|  
|[Практическое руководство. Отключение множественных активных результирующих наборов (функция MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)|Описывает отключение функции MARS при установке соединения.|  
|[Параметры соединения](../../connect/php/connection-options.md)|Содержит список параметров, которые допускаются в ассоциативном массиве, содержащем атрибуты подключения.|  
|[Поддержка LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)|Описывает поддержку [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] функции LocalDB, которая была добавлена в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|[Поддержка высокого уровня доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)|Описывается настройка приложения для использования функций высокого уровня доступности и аварийного восстановления, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|[Подключение к базе данных Microsoft Azure SQL](../../connect/php/connecting-to-microsoft-azure-sql-database.md)|Описывается подключение к базе данных SQL Azure.|  
|[Устойчивость подключений](../../connect/php/connection-resiliency.md)|Описывается функция устойчивости подключений, который восстанавливает прерванных соединений.|  

## <a name="see-also"></a>См. также:  
[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)  
