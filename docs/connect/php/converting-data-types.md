---
title: Преобразование типов данных
description: Узнайте, как указать типы данных и предоставить сведения о типах данных по умолчанию при использовании драйверов Майкрософт для PHP для SQL Server
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 508542ec-cc28-4a17-80f4-52325d6a48db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b72b4e61331754a0bfead58710709552652a176f
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680619"
---
# <a name="converting-data-types"></a>Преобразование типов данных
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] позволяет указать типы данных при отправке данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или извлечении их оттуда. Указание типов данных является необязательным. Если типы данных не указаны, используются типы по умолчанию. Приведенные в этом разделе статьи описывают, как указывать типы данных и предоставлять сведения о типах данных по умолчанию.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
|[Типы данных SQL Server по умолчанию](../../connect/php/default-sql-server-data-types.md)|Предоставляет сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию при отправке данных на сервер.|  
|[типы данных PHP по умолчанию;](../../connect/php/default-php-data-types.md)|Предоставляет сведения о типах данных PHP по умолчанию при извлечении данных с сервера.|  
|[Практическое руководство. Указание типов данных SQL Server](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)|Демонстрирует, как указать типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при отправке данных на сервер.|  
|[Практическое руководство. Указание типов данных PHP](../../connect/php/how-to-specify-php-data-types.md)|Демонстрирует, как указать типы данных PHP при извлечении данных с сервера.|  
|[Руководство. отправлять и извлекать данные UTF-8 с помощью встроенной поддержки UTF-8](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)|Демонстрирует, как использовать встроенную в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддержку данных UTF-8.<br /><br />Поддержка символов UTF-8 была добавлена в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии 1.1.|  
|[Практическое руководство. Отправка и получение ASCII-данных в Linux и macOS](../../connect/php/how-to-send-and-retrieve-ascii-data-in-linux-mac.md)|Демонстрирует, как применить в Linux и macOS встроенную в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддержку данных ASCII.<br /><br />Поддержка символов ASCII для сред, отличных от Windows, была добавлена в версии [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 5.2.|
  
## <a name="see-also"></a>См. также:  
[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)  
  
