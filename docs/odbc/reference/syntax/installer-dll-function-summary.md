---
title: Сводка по функциям библиотеки DLL установщика | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecb486f51caa97c715d54885c34575a60bfdfb83
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63231845"
---
# <a name="installer-dll-function-summary"></a>Сводка по функциям библиотеки DLL установщика
Ниже перечислены функции в DLL установщика. Дополнительные сведения о синтаксисе и семантике для каждой функции см. в разделе [Справочник по API библиотеки DLL установщика](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Задача|Имя функции|Цель|  
|----------|-------------------|-------------|  
|Установка ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Загружает DLL-файлов установки драйвера.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Возвращает список установленных драйверов.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Добавляет драйвер сведения о системе.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Возвращает целевой каталог для диспетчера драйверов.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Возвращает сведения об ошибках и состоянии для функций установщика.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Добавляет сведения о системе переводчика.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Позволяет библиотеку установки драйвера или перевода для сообщения об ошибках.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Удаляет драйвер из сведений о системе.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Удаляет компоненты core ODBC из сведений о системе.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Удаляет преобразователь из сведений о системе.|  
|Настройка источников данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Вызывает DLL-файлов установки драйвера.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Отображает диалоговое окно, чтобы добавить источник данных.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Извлекает режим конфигурации, указывающее, где операция Odbc.ini, список значений имени DSN в сведениях о системе.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Записывает сведения о системе значение.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Отображает диалоговое окно для выбора переводчика.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Отображает диалоговое окно для настройки источников данных и драйверы.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Считывает информацию из файла источников данных.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Удаляет источник данных по умолчанию.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Удаляет источник данных.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Задает режим конфигурации, который указывает, где запись Odbc.ini, список значений имени DSN в сведениях о системе.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Проверяет, длина и допустимость имени источника данных.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Добавляет источник данных.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Записывает сведения о файле источников данных.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Возвращает значение из информации о системе.|
