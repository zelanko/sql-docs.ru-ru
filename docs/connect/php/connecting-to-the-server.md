---
title: Подключение к серверу
description: Узнайте о различных методах подключения к базе данных с помощью драйверов Майкрософт для PHP для SQL Server.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c251a239-e0bd-4f45-9207-b76651072dd0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5a2ec027a72bd96b567b08639568b6ead8e5dc64
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410980"
---
# <a name="connecting-to-the-server"></a>Подключение к серверу
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Статьи, приведенные в этом разделе, описывают параметры и процедуры для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] может подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows или проверки подлинности SQL Server. По умолчанию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] пытаются подключиться к серверу с использованием проверки подлинности Windows.  

## <a name="in-this-section"></a>в этом разделе  

|Раздел|Описание|  
|---------|---------------|  
|[Руководство. Подключение с помощью проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md)|Описывает, как установить соединение с использованием проверки подлинности Windows.|  
|[Руководство. Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md) (Как установить подключение с использованием проверки подлинности SQL Server)|Описывает, как установить соединение с использованием проверки подлинности SQL Server.|  
|[Практическое руководство. Подключение с использованием проверки подлинности Azure Active Directory](../../connect/php/azure-active-directory.md)|Сведения о том, как настраивать режим проверки подлинности и подключаться с удостоверениями Azure Active Directory.|  
|[Практическое руководство. Подключение к заданному порту](../../connect/php/how-to-connect-on-a-specified-port.md)|Описывает, как подключиться к серверу через определенный порт.|  
|[Объединение подключений в пул](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)|Предоставляет сведения об использовании пулов подключений в драйвере.|  
|[Практическое руководство. Отключение множественных активных результирующих наборов (функция MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md)|Описывает отключение функции MARS при установке соединения.|  
|[Параметры подключения](../../connect/php/connection-options.md)|Содержит список параметров, которые допускаются в ассоциативном массиве, содержащем атрибуты подключения.|  
|[Поддержка LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)|Описывает поддержку [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] функции LocalDB, которая была добавлена в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|[Поддержка высокого уровня доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)|Описывается настройка приложения для использования функций высокого уровня доступности и аварийного восстановления, появившихся в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|[Подключение к базе данных Microsoft Azure SQL](../../connect/php/connecting-to-microsoft-azure-sql-database.md)|Описывается подключение к базе данных SQL Azure.|  
|[Устойчивость подключения](../../connect/php/connection-resiliency.md)|Обсуждение возможности устойчивости подключений, которая восстанавливает нарушенные подключения.|  

## <a name="see-also"></a>См. также:  
[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)  
