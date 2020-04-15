---
title: ODBC Визуальная FoxPro Настройка Диалог Box (ru) Документы Майкрософт
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
ms.openlocfilehash: ef7ac702a69342833c6dfffa0ffc9cdd0ac2857e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298084"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>Диалоговое окно настройки ODBC для Visual FoxPro
Диалоговый ящик **ODBC Visual FoxPro Setup** позволяет добавлять или изменять источник данных Visual FoxPro.  
  
 Чтобы загрузить драйвер, смотрите [визуальный FoxPro ODBC Драйвер скачать сайт](https://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Параметры диалогового окна  
 **Имя источника данных**  
 Введите имя, которое вы хотите использовать для источника данных.  
  
 **Описание**  
 Введите описание для источника данных.  
  
 **Тип базы данных**  
 Позволяет выбрать тип базы данных, к какой базе данных вы хотите подключить источник данных.  
  
 **Визуальная база данных FoxPro (. DBC)**  
 Уточняется, что источник данных подключается к [базе данных](../../odbc/microsoft/visual-foxpro-terminology.md) Visual FoxPro (файл.dbc) и ко всем таблицам и локальным представлениям в базе данных.  
  
 **Бесплатный каталог таблицы**  
 Упомянет, что источник данных подключается к каталогу [свободных таблиц.](../../odbc/microsoft/visual-foxpro-terminology.md) Любые таблицы [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md) в одном и том же каталоге игнорируются функциями каталога ODBC, такими как [S'LColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) или [S'LTables.](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) Таблицы баз данных могут быть доступны с помощью s-L SELECT выписок, отправляемых через [S'L'LExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) и [S'LExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Путь**  
 Отображает путь и имя базы данных или каталог свободных таблиц, к которым подключается источник данных.  
  
 **Обзор**  
 Позволяет искать систему и сеть для базы данных или каталога, к которому вы хотите подключить источник данных.  
  
 **Параметры**  
 Расширяет диалоговую коробку, чтобы можно было установить параметры Visual FoxPro ODBC Driver.  
  
## <a name="driver"></a>Драйвер  
 **Последовательность сопоставления**  
 Последовательность, в которой сортируются поля. Последовательности по умолчанию отражают последовательности, поддерживаемые языковой версией операционной системы. Список поддерживаемых последовательностей сопоставления см. [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Монопольно**  
 При выборе этого флажка драйвер открывает базу данных Visual FoxPro исключительно при доступе к данным с помощью источника данных. Другие пользователи не могут получить доступ к базе данных или таблицам в базе данных, пока база данных открыта исключительно. Таблицы в исключительно открытой базе данных открываются как SHARED. Чтобы открыть стол исключительно, используйте команду [SET EXCLUSIVE.](../../odbc/microsoft/set-exclusive-command.md) Этот флажок отключен, когда **тип базы данных** установлен в **каталоге Free Table.**  
  
 **Null**  
 Определяет, позволяют ли столбцы, созданные с помощью ALTER TABLE и CREATE TABLE, нулевыми значениями. Если вы установите Null ON, INSERT - S'L вставляет нулевую стоимость в любой столбец, не включенный в INSERT - S'L... VALUE положение. Заготовка вставляется, если Null является OFF. Вы также можете управлять этой опцией через пройденную строку соединения, как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **Удалены**  
 Определяет, возвращаются ли строки, помеченные как удаленные. Вы также можете управлять этой опцией через пройденную строку соединения, как в следующем коде:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Извлечение данных в фоновом режиме**  
 Определяет, будут ли записи извлечены в фоновом режиме (прогрессивный извлечение) или ваше приложение будет ждать, пока не будут извлечены все записи в наборе результатов.
