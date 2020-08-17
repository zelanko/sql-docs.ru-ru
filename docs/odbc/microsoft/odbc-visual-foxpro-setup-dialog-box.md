---
description: Диалоговое окно настройки ODBC для Visual FoxPro
title: Диалоговое окно «Установка ODBC в Visual FoxPro» | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2083f76300ed19e047b0a138aed6c65ecef4da3d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340710"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Диалоговое окно настройки ODBC для Visual FoxPro
Диалоговое окно **установки ODBC Visual FoxPro** позволяет добавлять или изменять источник данных Visual FoxPro.  
  
 Сведения о загрузке драйвера см. [на веб-сайте загрузки драйверов ODBC для Visual FoxPro](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Параметры диалогового окна  
 **Имя источника данных**  
 Введите имя, которое будет использоваться для источника данных.  
  
 **Описание**  
 Введите описание источника данных.  
  
 **Тип базы данных**  
 Позволяет выбрать тип базы данных, к которой должен подключаться источник данных.  
  
 **База данных Visual FoxPro (. DBc**  
 Указывает, что источник данных подключается к [базе данных](../../odbc/microsoft/visual-foxpro-terminology.md) Visual FoxPro (DBC-файлу) и ко всем таблицам и локальным представлениям в базе данных.  
  
 **Каталог свободной таблицы**  
 Указывает, что источник данных подключается к каталогу [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md). Любые таблицы [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) в одном каталоге игнорируются ФУНКЦИЯМИ каталогов ODBC, такими как [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) или [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Доступ к таблицам базы данных можно получить с помощью инструкций SQL SELECT, отправленных через [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) и [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Путь**  
 Отображает путь и имя базы данных, а также каталог свободных таблиц, к которым подключается источник данных.  
  
 **Обзор**  
 Позволяет выполнять поиск в системе и в сети базы данных или каталога, к которым необходимо подключить источник данных.  
  
 **Параметры**  
 Раскрывает диалоговое окно, чтобы можно было задать параметры драйвера ODBC для Visual FoxPro.  
  
## <a name="driver"></a>Драйвер  
 **Порядок сортировки**  
 Последовательность, в которой сортируются поля. Последовательности по умолчанию соответствуют последовательностям, поддерживаемым языковой версией операционной системы. Список поддерживаемых последовательностей сортировки см. в разделе [Set COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Монопольный доступ**  
 Если этот флажок установлен, драйвер открывает базу данных Visual FoxPro исключительно при доступе к данным с помощью источника данных. Другие пользователи не могут получить доступ к базе данных или таблицам в базе данных, пока база данных открыта только для использования. Таблицы в монопольно открытой базе данных открываются как общие. Чтобы открыть только таблицу, используйте команду [Set Exclusive](../../odbc/microsoft/set-exclusive-command.md) . Этот флажок недоступен, если для параметра **тип базы данных** задано значение **бесплатный каталог таблицы**.  
  
 **Null**  
 Определяет, разрешены ли значения NULL для столбцов, созданных с помощью инструкции ALTER TABLE и CREATE TABLE. Если задать значение NULL ON, инструкция INSERT-SQL вставит значение NULL в любой столбец, не включенный в инструкцию INSERT-SQL... Предложение VALUE. Если значение NULL равно OFF, вставляется пустая строка. Этот параметр также можно контролировать с помощью переданной строки подключения, как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Удалено**  
 Определяет, возвращаются ли строки, помеченные как удаленные. Этот параметр также можно контролировать с помощью переданной строки подключения, как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Получить данные в фоновом режиме**  
 Определяет, будут ли записи выбираться в фоновом режиме (прогрессивная выборка), или ваше приложение будет ожидать получения всех записей в результирующем наборе.
