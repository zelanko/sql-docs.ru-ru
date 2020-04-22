---
title: Шаг 1. Настройка среды для PHP
description: На шаге 1 этого руководства по началу работы предполагается установка PHP, Microsoft ODBC Driver for SQL Server и настройка среды разработки.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0bce6022-00bd-45c6-9671-eaa9dfa395a8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88eb2c2c67eac3ecd9fba2c79c143de28cf60d22
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633175"
---
# <a name="step-1-configure-environment-for-php-development"></a>Шаг 1. Настройка среды для разработки на PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]




* Выберите используемую версию драйвера PHP, исходя из версии вашей среды, как указано здесь:  [Системные требования драйверов Майкрософт для PHP для SQL Server](system-requirements-for-the-php-sql-driver.md)
* Скачайте и установите соответствующий драйвер PHP отсюда: [Скачать драйвер Microsoft PHP](https://www.microsoft.com/download/details.aspx?id=20098)  
* Скачайте и установите соответствующий драйвер ODBC отсюда:  [Скачивание драйвера ODBC Driver for SQL Server](../odbc/download-odbc-driver-for-sql-server.md)  
* Настройте драйвер PHP и веб-сервер для конкретной операционной системы.

### <a name="windows"></a>Windows  
  

* Настройте загрузку драйвера PHP, как описано здесь: [Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md) 
* Настройте службы IIS для размещения приложений PHP, как описано здесь: [Настройка служб IIS для драйверов Майкрософт для PHP для SQL Server](../../connect/php/configuring-iis-for-php-sql-driver.md)

### <a name="linux-and-macos"></a>Linux и macOS


*   Настройте загрузку драйвера PHP и настройте веб-сервер для размещения приложений PHP, как описано здесь: [Учебник по установке драйверов PHP для Linux и macOS](../../connect/php/installation-tutorial-linux-mac.md)
