---
title: "ODBC Jet SQLConfigDataSource (драйвер Excel) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Excel Driver
- Excel driver [ODBC], SqlConfigDataSource
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a4d5d0b2feb0a09aafeb441c6b33260e4f0738b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (драйвер Excel)
> [!NOTE]  
>  В этом разделе сведения драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLConfigDataSource** функцию, которая будет использоваться для добавления, изменения или удаления источника данных динамически используются следующие ключевые слова.  
  
|Ключевое слово|Description|  
|-------------|-----------------|  
|DBQ|Для драйвера Microsoft Excel при доступе к Microsoft Excel 5.0 или более поздние версии файлов, имя файла рабочей книги.<br /><br /> Таким образом задается один и тот же параметр как **базы данных** в диалоговом окне программы установки.|  
|ЕГО ЗНАЧЕНИЯ|Строка пути к каталогу.<br /><br /> Таким образом задается один и тот же параметр как **Выбор каталога** или **Выбор книги** в диалоговом окне программы установки.|  
|DESCRIPTION|Описание данных в источнике данных.<br /><br /> Таким образом задается один и тот же параметр как **описание** в диалоговом окне программы установки.|  
|DRIVER|Строка пути к DLL-Библиотека драйвера.|  
|DRIVERID|Целочисленный идентификатор для драйвера.<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL|Тип, например, Excel 3.0, Excel 4.0, Excel 5.0, Excel 7.0, Excel 97, Excel 2000 или Excel 2003 файла.|  
|FIRSTROWHASNAMES|Указывает, содержат ли ячейки первой строки диапазона дат, имен столбцов для таблицы (1) или нет (0).|  
|MAXSCANROWS|Число строк для просмотра при задании типа данных столбца на основе существующих данных.<br /><br /> Можно ввести число от 1 до 16 для строк для сканирования. По умолчанию используется значение 8. Если свойство имеет значение 0, просматриваются все строки. (Число за пределами ограничение будет возвращена ошибка.)<br /><br /> Таким образом задается один и тот же параметр как **строк для просмотра** в диалоговом окне программы установки.|  
|READONLY|Значение TRUE, чтобы сделать файл доступным только для чтения; Значение FALSE, чтобы сделать файл не только для чтения.<br /><br /> Таким образом задается один и тот же параметр как **только для чтения** в диалоговом окне программы установки.|  
|ПОТОКИ|Число фоновых потоков, используемых механизмом. Для драйвера Microsoft Access это значение по умолчанию — 3, но могут быть изменены. DBASE MicrosoftExceldriver это значение равно 3 и не может быть изменено.<br /><br /> Таким образом задается один и тот же параметр как **потоков** в диалоговом окне программы установки.|

