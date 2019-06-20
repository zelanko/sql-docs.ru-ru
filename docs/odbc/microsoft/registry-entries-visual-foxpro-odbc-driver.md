---
title: Записи реестра (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de287802693adb18e39509fdc0e7577d05984949
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63316827"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Записи реестра (драйвер ODBC для Visual FoxPro)
При установке драйвера ODBC для Visual FoxPro, программа установки обновляет в системном реестре, в разделе реестра HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, чтобы добавить новый ключ с именем драйвера Microsoft Visual FoxPro. По этому ключу добавляются значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|«YYN»|  
|Драйвер|REG_SZ|Путь к файлу vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"*.dbf,\*.cdx,\*.fpt"|  
|FileUsage|REG_SZ|"1"|  
|Установка|REG_SZ|Путь к файлу vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 Программа установки также добавляет ключ «Visual FoxPro Files», представляющий драйвера по умолчанию для Visual FoxPro, к ключу HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini системы. В этом разделе программа установки добавляет значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|Драйвер|REG_SZ|Путь к файлу vfpodbc.dll|  
  
 Каждый раз при добавлении источника данных Visual FoxPro ODBC в конфигурацию ODBC новый ключ добавляется имя для этого источника данных. Значения для источника данных соответствуют значениям, заданным в **настройки ODBC для Visual FoxPro** диалоговое окно, как показано в следующей таблице.  
  
|Имя значения (ключевое слово)|Тип значения|Значение|  
|----------------------------|----------------|-----------|  
|Разобрать по копиям|REG_SQ|Любой поддерживаемый упорядоченной последовательности|  
|Описание|REG_SZ|Описание источника данных пользователя|  
|Драйвер||Путь к файлу vfpodbc.dll|  
|Монопольно||"Да" или "Нет".|  
|BackgroundFetch||"Да" или "Нет".|  
|SourceDB|REG_SZ|Путь. Файл DBC|  
|Тип источника|REG_SZ|«DBC» или «DBF»|  
  
 Эти сведения не доступ напрямую. любой администрирования реестра обрабатывается администратором ODBC, если добавить, изменить или удалить источник данных.  
  
 Некоторые из этих ключевых слов и значений можно использовать в качестве параметров [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) функции ODBC API.
