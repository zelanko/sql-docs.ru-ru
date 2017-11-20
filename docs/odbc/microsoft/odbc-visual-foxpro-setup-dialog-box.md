---
title: "Диалоговое окно установки Visual FoxPro ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 22208bd706e7b8966f54a501e9580b35d99a0555
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Диалоговое окно установки Visual FoxPro ODBC
**Установки Visual FoxPro ODBC** диалоговое окно позволяет добавить или изменить источник данных Visual FoxPro.  
  
 Чтобы загрузить драйвер, в разделе [на сайт загрузки драйвера ODBC для Visual FoxPro](http://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Параметры диалогового окна  
 **Имя источника данных**  
 Введите имя, которое будет использоваться для источника данных.  
  
 **Description**  
 Введите описание для источника данных.  
  
 **Тип базы данных**  
 Позволяет выбрать тип базы данных, необходимо подключиться к источнику данных.  
  
 **База данных Visual FoxPro (. DBC)**  
 Указывает, что источник данных подключается к Visual FoxPro [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) (.dbc-файл) и для всех таблиц и локальных представлений в базе данных.  
  
 **Освободить таблице directory**  
 Указывает, что источник данных подключается к каталогу [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md). Любой [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) таблицы в том же каталоге игнорируются функций каталога ODBC, такие как [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) или [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Таблицы базы данных может осуществляться с помощью инструкций SQL SELECT, отправленных [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) и [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Путь**  
 Отображает путь и имя базы данных или каталога свободных таблиц, к которым соединяется с источником данных.  
  
 **Обзор**  
 Позволяет найти системы и сети для базы данных или каталога, к которому требуется подключение к источнику данных.  
  
 **Параметры**  
 Разверните диалоговое окно, чтобы выбрать параметры драйвера ODBC для Visual FoxPro.  
  
## <a name="driver"></a>Драйвер  
 **Порядок сортировки**  
 Последовательность, в которой отсортированы поля. Последовательности по умолчанию отражают последовательностей, поддерживаемом версией языка операционной системы. Список поддерживаемых упорядоченной последовательности см. в разделе [ЗАДАТЬ COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Монопольно**  
 Если этот флажок установлен, драйвер открывает Visual FoxPro базы данных только в том случае, когда осуществляется доступ к данным с использованием источника данных. Другие пользователи не могут открывать базы данных или таблицы в базе данных, пока база данных открыта только. Таблицы в базе данных только открытые, открываются как общий. Чтобы открыть таблицу в монопольном режиме, используйте [УСТАНОВИТЬ МОНОПОЛЬНУЮ](../../odbc/microsoft/set-exclusive-command.md) команды. Этот флажок недоступен при **тип базы данных** равно **directory свободной таблице**.  
  
 **Значение NULL**  
 Определяет, является ли столбцы, созданные с помощью инструкции ALTER TABLE и CREATE TABLE допускает значения null. Если задать значение Null, ON вставки — SQL вставляет значение null в столбец, не включенные в инструкции INSERT — SQL... ЗНАЧЕНИЕ предложения. Пустое вставляется в том случае, если Null имеет значение OFF. Также можно выбрать этот параметр в строке подключения, переданный как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Удален**  
 Определяет, возвращаются ли строки, помечаются как удаленные. Также можно выбрать этот параметр в строке подключения, переданный как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Выборка данных в фоновом режиме**  
 Определяет, будут выбираться записи в фоновом режиме (последовательная выборка) или приложение ожидает, пока не будут выбраны все записи в результирующем наборе.

