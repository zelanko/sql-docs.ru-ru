---
title: Установщик DLL Функция Резюме (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddaf20334a84833433961a49e17724d354945c5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298774"
---
# <a name="installer-dll-function-summary"></a>Сводка по функциям библиотеки DLL установщика
В следующей таблице описаны функции в установщике DLL. Для получения дополнительной информации о синтаксисе [Installer DLL API Reference](../../../odbc/reference/syntax/installer-dll-api-reference-function.md)и семантике для каждой функции, см.  
  
|Задача|Имя функции|Цель|  
|----------|-------------------|-------------|  
|Установка ODBC|[СЗЛКонзигДрайвер](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Загружает настроенную установку DLL, специфичную для драйвера.|  
||[СЗЛТЕтАзидДрайвери](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Возвращает список установленных драйверов.|  
||[СЗЛУстантЛисонДрайверЭкс](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Добавляет драйвер в системную информацию.|  
||[СЗЛУстановитьДрайверМенеджер](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Возвращает целевой каталог для менеджера драйвера.|  
||[СЗЛУСтангерОшибка](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Возвращает информацию об ошибке или статусе для функций установки.|  
||[СЗЛУстантинТрансрекс](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Добавляет переводчика в системную информацию.|  
||[СЗЛПостУстановитьerОшибка](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Позволяет библиотеке настройки драйвера или переводчика сообщать об ошибках.|  
||[СЗЛЛиУМДрайвер](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Удаляет информацию о драйвере из системы.|  
||[СЗЛУдалениеДрайверМенеджер](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Удаляет основные компоненты ODBC из системной информации.|  
||[СЗЛУдалитьПереводчик](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Удаляет информацию о переводе из системы.|  
|Настройка источников данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Вызывает настроенную установку DLL для конкретного водителя.|  
||[СЗЛСоздатьДатаИсточник](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Отображает диалоговый ящик для добавления источника данных.|  
||[СЗЛГетКонигМоид](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Извлекает режим конфигурации, указывающий, где в системе находится запись Odbc.ini, в которой перечислены значения DSN.|  
||[СЗЛГетПриТПрогрядТст](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Записывает значение для системной информации.|  
||[СЗЛГетПереводчик](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Отображает диалоговую коробку для выбора переводчика.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Отображает диалоговую коробку для настройки источников данных и драйверов.|  
||[СЗЛРедРедЕДСН](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Читает информацию из файла DSNs.|  
||[СЗЛУдалениеDefaultDataИсточник](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Удаляет источник данных по умолчанию.|  
||[СЗЛССНСНИзинини](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Удаляет источник данных.|  
||[СЗЛСККонзигМой](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Устанавливает режим конфигурации, указывающий, где в системе находится запись Odbc.ini, в которой перечислены значения DSN.|  
||[СЗЛЛиАДСН](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Проверяет длину и достоверность имени источника данных.|  
||[СЗЛДуНТСНОниИ](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Добавляет источник данных.|  
||[СЗЛСрайтФилдсн](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Записывает информацию для файла DSNs.|  
||[СЗЛСНайтПритПритПрогрядТ](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Получает значение из системной информации.|
