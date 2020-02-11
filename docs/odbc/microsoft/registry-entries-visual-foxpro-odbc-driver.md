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
ms.openlocfilehash: 00a24ffca764c029b87470b7aa07d15f33b4c673
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996451"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Записи реестра (драйвер ODBC для Visual FoxPro)
При установке драйвера ODBC для Visual FoxPro программа установки обновляет реестр системы, в разделе реестра HKEY_LOCAL_MACHINE \Софтваре\одбк\одбЦинст.ини, чтобы добавить новый раздел под названием драйвер Microsoft Visual FoxPro. В этом разделе добавляются значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|апилевел|REG_SZ|1|  
|коннектфунктионс|REG_SZ|"ИИН"|  
|Драйвер|REG_SZ|Системный путь к файлу вфподбк. dll|  
|DriverODBCVer|REG_SZ|"02,50"|  
|филикстнс|REG_SZ|"*. dbf,\*. cdx,\*. ФПТ"|  
|филеусаже|REG_SZ|1|  
|Установка|REG_SZ|Системный путь к файлу вфподбк. dll|  
|скллевел|REG_SZ|0|  
  
 Программа установки также добавляет ключ "Visual FoxPro Files", представляющий стандартный драйвер Visual FoxPro, в систему HKEY_CURRENT_USER ключ \Софтваре\одбк\одбк.ини. В этом разделе Программа установки добавляет значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|Драйвер|REG_SZ|Системный путь к файлу вфподбк. dll|  
  
 Каждый раз при добавлении источника данных ODBC Visual FoxPro в конфигурацию ODBC для этого имени источника данных добавляется новый ключ. Значения для источника данных соответствуют значениям, заданным в диалоговом окне **установки ODBC Visual FoxPro** , как указано в следующей таблице.  
  
|Имя значения (ключевое слово)|Тип значения|Значение|  
|----------------------------|----------------|-----------|  
|Разобрать по копиям|REG_SQ|Все поддерживаемые последовательности сортировки|  
|Description|REG_SZ|Описание источника данных для пользователя|  
|Драйвер||Системный путь к файлу вфподбк. dll|  
|Монопольная блокировка||"Да" или "Нет".|  
|баккграундфетч||"Да" или "Нет".|  
|SourceDB|REG_SZ|Путь к. Файл DBC|  
|Тип источника|REG_SZ|"DBC" или "DBF"|  
  
 Не следует обращаться к этим сведениям напрямую; Администрирование реестра осуществляется администратором ODBC при добавлении, изменении или удалении источника данных.  
  
 Некоторые из этих ключевых слов и значений можно использовать в качестве параметров функции API ODBC [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) .
