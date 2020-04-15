---
title: Регистрационные записи (Визуальный водитель FoxPro ODBC) Документы Майкрософт
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
ms.openlocfilehash: bd2d419a94c45a872789e095b014159b41d7c217
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304841"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Записи реестра (драйвер ODBC для Visual FoxPro)
При установке Visual FoxPro ODBC Driver программа установки обновляет реестр вашей системы, в ключе реестра HKEY_LOCAL_MACHINE»SOFTWARE-ODBC-ODBCInst.ini, чтобы добавить новый ключ под названием Microsoft Visual FoxPro Driver. Под этим ключом добавляются значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|1|  
|ПодключениеФункции|REG_SZ|"YYN"|  
|Драйвер|REG_SZ|Системный путь к файлу vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|".dbf,\*.cdx,\*.fpt"|  
|FileUsage|REG_SZ|1|  
|Настройка|REG_SZ|Системный путь к файлу vfpodbc.dll|  
|СЗЛУЛиум|REG_SZ|0|  
  
 Программа установки также добавляет ключ "Visual FoxPro Файлы", представляющие драйвер Visual FoxPro по умолчанию, в HKEY_CURRENT_USER-SOFTWARE-ODBC-Odbc.ini ключ. В соответствии с этим ключом программа установки добавляет значения, описанные в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|Драйвер|REG_SZ|Системный путь к файлу vfpodbc.dll|  
  
 Каждый раз, когда вы добавляете visual FoxPro ODBC источник данных в конфигурацию ODBC, новый ключ добавляется для этого имени источника данных. Значения для источника данных соответствуют значениям, установленным в диалоговом окне **ODBC Visual FoxPro Setup,** указанному в следующей таблице.  
  
|Значение имени (ключевое слово)|Тип значения|Значение|  
|----------------------------|----------------|-----------|  
|Разобрать по копиям|REG_SQ|Любая поддерживаемая последовательность коллажа|  
|Описание|REG_SZ|Описание источником данных для пользователей|  
|Драйвер||Системный путь к файлу vfpodbc.dll|  
|Монопольная блокировка||"Да" или "Нет".|  
|BackgroundFetch||"Да" или "Нет".|  
|SourceDB|REG_SZ|Путь к . DBC файл|  
|Тип источника|REG_SZ|"DBC" или "DBF"|  
  
 Вы не должны получать доступ к этой информации напрямую; любое администрирование реестра обрабатывается администратором ODBC при добавлении, изменении или удалении источника данных.  
  
 Некоторые из этих ключевых слов и значений можно использовать в качестве параметров в функции API [ODBC S'LDriverConnect.](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)
