---
description: Записи реестра (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc4c5d617590e6435d99756b159c6049551d2d69
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340350"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Записи реестра (драйвер ODBC для Visual FoxPro)
При установке драйвера ODBC для Visual FoxPro программа установки обновляет реестр системы в разделе реестра HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, чтобы добавить новый раздел под названием драйвер Microsoft Visual FoxPro. В этом разделе добавляются значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|апилевел|REG_SZ|"1"|  
|коннектфунктионс|REG_SZ|"ИИН"|  
|Драйвер|REG_SZ|Системный путь к файлу vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02,50"|  
|филикстнс|REG_SZ|"*. dbf, \* . cdx, \* . ФПТ"|  
|филеусаже|REG_SZ|"1"|  
|Настройка|REG_SZ|Системный путь к файлу vfpodbc.dll|  
|скллевел|REG_SZ|"0"|  
  
 Программа установки также добавляет ключ "Visual FoxPro Files", представляющий драйвер Visual FoxPro по умолчанию, в ключ системы HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini. В этом разделе Программа установки добавляет значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|Драйвер|REG_SZ|Системный путь к файлу vfpodbc.dll|  
  
 Каждый раз при добавлении источника данных ODBC Visual FoxPro в конфигурацию ODBC для этого имени источника данных добавляется новый ключ. Значения для источника данных соответствуют значениям, заданным в диалоговом окне **установки ODBC Visual FoxPro** , как указано в следующей таблице.  
  
|Имя значения (ключевое слово)|Тип значения|Значение|  
|----------------------------|----------------|-----------|  
|Разобрать по копиям|REG_SQ|Все поддерживаемые последовательности сортировки|  
|Описание|REG_SZ|Описание источника данных для пользователя|  
|Драйвер||Системный путь к файлу vfpodbc.dll|  
|Монопольная блокировка||"Да" или "Нет".|  
|баккграундфетч||"Да" или "Нет".|  
|SourceDB|REG_SZ|Путь к. Файл DBC|  
|Тип источника|REG_SZ|"DBC" или "DBF"|  
  
 Не следует обращаться к этим сведениям напрямую; Администрирование реестра осуществляется администратором ODBC при добавлении, изменении или удалении источника данных.  
  
 Некоторые из этих ключевых слов и значений можно использовать в качестве параметров функции API ODBC [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) .
