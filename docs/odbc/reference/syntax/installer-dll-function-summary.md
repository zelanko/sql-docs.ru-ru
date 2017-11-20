---
title: "Сводка по функциям DLL установщика | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 42b2338cafa53a2813929c3d674d9ed0a9789bdb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="installer-dll-function-summary"></a>Сводка по функциям DLL установщика
Ниже перечислены функции в программе установки библиотеки DLL. Дополнительные сведения о синтаксисе и семантику для каждой функции см. в разделе [Справочник по API библиотеки DLL установщика](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Задача|Имя функции|Назначение|  
|----------|-------------------|-------------|  
|Установка ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Загружает DLL-файлов установки драйвера.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Возвращает список установленных драйверов.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Добавляет сведения о системе драйвер.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Возвращает целевой каталог для диспетчера драйверов.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Возвращает ошибки или состояния сведения о функции установщика.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Добавляет сведения о системе преобразователя.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Позволяет библиотека установки драйвера или транслятор отчетов об ошибках.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Удаляет драйвер из сведений о системе.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Удаляет компоненты ядра ODBC из сведений о системе.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Удаляет преобразователь из сведений о системе.|  
|Настройка источников данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Вызов DLL-файлов установки драйвера.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Отображает диалоговое окно для добавления источника данных.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Извлекает режим конфигурации, указывающей место записи Odbc.ini со списком значений источника данных сведений о системе.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Записывает сведения о системе значение.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Отображает диалоговое окно для выбора переводчика.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Отображает диалоговое окно для настройки источников данных и драйверы.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Считывает данные из файла источников данных.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Удаление источника данных по умолчанию.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Удаление источника данных.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Задает режим конфигурации, который указывает, где в сведениях о системе Odbc.ini запись со списком значений источника данных.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Проверяет, длина и допустимость имени источника данных.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Добавление источника данных.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Записывает сведения в файл источников данных.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Возвращает значение из сведений о системе.|

