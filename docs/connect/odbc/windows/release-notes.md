---
title: Release Notes (драйвер ODBC для SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
caps.latest.revision: 7
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 0e99381224c03bf185044d57cc4b415fcfaedd3b
ms.sourcegitcommit: 9229fb9b37616e0b73e269d8b97c08845bc4b9f3
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/13/2018
ms.locfileid: "39024230"
---
# <a name="release-notes"></a>Заметки о выпуске
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Заметки о выпуске Microsoft ODBC Driver for SQL Server для Windows.  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows

**Функции, добавленные**:

Классификация данных для базы данных Azure SQL и SQL Server

[Исправления ошибок](../bug-fixes.md)

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows

**Функции, добавленные**:

Поддержка `SQL_COPT_SS_CEKCACHETTL` и `SQL_COPT_SS_TRUSTEDCMKPATHS` атрибуты соединения (Дополнительные сведения см. в разделе [использование функции Always Encrypted с драйвером ODBC для SQL Server](../using-always-encrypted-with-the-odbc-driver.md))
- `SQL_COPT_SS_CEKCACHETTL` Разрешает управление времени, который существует в локальном кэше ключей шифрования столбцов, а также его очистки
- `SQL_COPT_SS_TRUSTEDCMKPATHS` Позволяет приложению ограничить операции AE только использовать указанный список главных ключей столбцов


Поддержка интерактивной проверки подлинности Azure Active Directory

[Исправления ошибок](../bug-fixes.md)


## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows

**Функции, добавленные**:

Поддержка постоянного шифрования для BCP API

Новый атрибут строки подключения UseFMTOnly драйвер использовать устаревшие метаданные в особых случаях, требующих временных таблиц.

Поддержка управляемый экземпляр Azure SQL (расширенная закрытая Предварительная версия). 
> [!NOTE]
> Существует ряд различий, при использовании управляемого экземпляра:
> -   FILESTREAM не поддерживается 
> -   Доступа к локальной файловой системы не поддерживается, но необходимые для таких вещей, как tracefiles 
> -   Создание определяемого пользователем ТИПА из локального пути не поддерживается. 
> -   Встроенная проверка подлинности Windows не поддерживается 
> -   DTC не поддерживается 
> -   Учетная запись «sa» не присутствует (по умолчанию учетная запись называется «cloudSA»)
> -   Ошибка маркера потока табличных данных (0xAA) возвращает неправильное имя сервера
> -   Специальные символы в имени базы данных не поддерживаются. 
> -   MODIFY NAME инструкции ALTER DATABASE [dbname1] = [dbname2] не поддерживается.
> -   Сообщения об ошибках всегда отображаются на английском языке, вне зависимости от языка параметры (то же, как в Azure) 
  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows  
 ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] добавлена поддержка [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) и [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) при использовании в сочетании с Microsoft SQL Server 2016.  Соответствующие соединения, регулирования количества запросов ключевые слова и атрибуты описаны в [драйвер Aware Connection Pooling in драйвер ODBC для SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows  
 ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] включает прежние функции от драйвера ODBC 11 для SQL Server и добавляет поддержку для Microsoft SQL Server 2016.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Новые возможности [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows  
 ODBC Driver 11 для SQL Server содержит новые [функции](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md), а также все функции, доступные в ODBC в SQL Server 2012 Native Client.  
