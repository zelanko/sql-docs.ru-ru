---
title: Диалоговое окно настройки Visual FoxPro ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35e9da17a9c3980470cfd3dcbb22b4069afec640
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233587"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Диалоговое окно настройки ODBC для Visual FoxPro
**Настройки ODBC для Visual FoxPro** диалоговое окно позволяет добавить или изменить источник данных Visual FoxPro.  
  
 Чтобы загрузить драйвер, см. в разделе [на сайт загрузки драйвера ODBC для Visual FoxPro](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Параметры диалогового окна  
 **Имя источника данных**  
 Введите имя, которое вы хотите использовать для источника данных.  
  
 **Описание**  
 Введите описание для источника данных.  
  
 **Тип базы данных**  
 Позволяет выбрать тип требуется источник данных для подключения к базе данных.  
  
 **Базы данных Visual FoxPro (. ДВУХБАЙТОВЫЕ СИМВОЛЫ)**  
 Указывает, что источник данных подключается к Visual FoxPro [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) (.dbc файл) и для всех таблиц и локальных представлений в базе данных.  
  
 **Бесплатный доступ к таблице directory**  
 Указывает, что источник данных подключается к каталогу [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md). Любой [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) таблиц в одном каталоге игнорируются функций каталога ODBC, такие как [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) или [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Таблицы базы данных может осуществляться с помощью инструкций SQL SELECT, отправленных через [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) и [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Путь**  
 Отображает путь и имя для базы данных или в каталоге свободного таблиц, к которым подключается источника данных.  
  
 **Обзор**  
 Позволяет найти системы и сети для базы данных или каталога, к которому требуется подключение к источнику данных.  
  
 **Параметры**  
 Разверните диалоговое окно, таким образом, можно задать параметры драйвера ODBC для Visual FoxPro.  
  
## <a name="driver"></a>Драйвер  
 **Порядок сортировки**  
 Последовательность, в которой сортируется поля. Последовательности по умолчанию отражают последовательностей, поддерживаемом версией языка операционной системы. Список поддерживаемых упорядоченной последовательности, см. в разделе [ЗАДАТЬ COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Монопольно**  
 Если этот флажок установлен, драйвер открывает базу данных Visual FoxPro, исключительно в том случае, когда осуществляется доступ к данным с использованием источника данных. Другим пользователям не может получить доступ к базе данных или таблицы в базе данных хотя база данных открыта только. Таблицы в монопольном режиме открытую базу данных, открываются как SHARED. Чтобы открыть таблицу в монопольном режиме, используйте [УСТАНОВИТЬ МОНОПОЛЬНУЮ](../../odbc/microsoft/set-exclusive-command.md) команды. Этот флажок не установлен при **тип базы данных** присваивается **directory свободной таблице**.  
  
 **Null**  
 Определяет, разрешает ли столбцы, созданные с помощью инструкции ALTER TABLE и CREATE TABLE значения null. Если задано значение Null, ON, инструкции INSERT - SQL вставляет значение null в любой столбец, не включается в инструкции INSERT - SQL... ЗНАЧЕНИЕ предложения. Пустое вставляется в том случае, если Null имеет значение OFF. Вы также можете управлять этот параметр через переданной строки подключения как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Удален**  
 Определяет, возвращаются ли строки, помечаются как удаленные. Вы также можете управлять этот параметр через переданной строки подключения как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Выборка данных в фоновом режиме**  
 Определяет, записей, полученных в результате в фоновом режиме (последовательная выборка) или приложение будет ожидать, пока не будут выбраны все записи в результирующем наборе.
