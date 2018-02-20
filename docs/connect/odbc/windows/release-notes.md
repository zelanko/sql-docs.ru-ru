---
title: "Заметки о выпуске | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 44c73c4d632fd434fcd296dc6fc2cc70af26086c
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
---
# <a name="release-notes"></a>Заметки о выпуске
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Заметки о выпуске Microsoft ODBC Driver for SQL Server для Windows.  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] 17 драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows

**Добавлены возможности**:

Всегда зашифровано поддержку BCP API

Новый атрибут строки подключения UseFMTOnly драйвер для использования устаревших метаданных в особых случаях, требующие временных таблиц.

Поддержка управляемого экземпляра Azure SQL (расширенные получения личной предварительной версии). 
> [!NOTE]
> Существует ряд различий при использовании управляемого экземпляра.
> -   FILESTREAM не поддерживается 
> -   Доступа к локальной файловой системе не поддерживается, но требуется для таких вещей, как tracefiles 
> -   Создание определяемого пользователем ТИПА из локального пути не поддерживается. 
> -   Встроенная проверка подлинности Windows не поддерживается. 
> -   DTC не поддерживается. 
> -   Учетная запись «sa» не указан (по умолчанию учетная запись называется «cloudSA»)
> -   Ошибка маркера потока табличных данных (0xAA) возвращает указано неправильное имя сервера
> -   Специальные символы в имени базы данных не поддерживаются. 
> -   [Dbname1] ALTER DATABASE MODIFY NAME = [dbname2] не поддерживается.
> -   Сообщения об ошибках всегда отображаются на английском языке независимо от языка параметров (то же, как Azure) 
  
## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows  
 ODBC Driver 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] добавляет поддержку для [постоянного шифрования](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) и [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) при использовании в сочетании с Microsoft SQL Server 2016.  Соответствующие соединения, регулирования количества запросов ключевые слова или атрибуты описаны в [драйвер Aware Connection Pooling в драйвере ODBC для SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows  
 ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] включает предыдущие функциональные возможности драйвера ODBC 11 для SQL Server и добавляет поддержку для Microsoft SQL Server 2016.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC 11 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows  
 ODBC Driver 11 для SQL Server содержит новые [функции](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md) а также все функции, доступные в ODBC в собственном клиенте SQL Server 2012.  
