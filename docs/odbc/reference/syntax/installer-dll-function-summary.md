---
description: Сводка по функциям библиотеки DLL установщика
title: Сводка по функциям DLL установщика | Документация Майкрософт
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
ms.openlocfilehash: 3666808659abb29a1f5a1eb1e8be62e8cf0507f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461236"
---
# <a name="installer-dll-function-summary"></a>Сводка по функциям библиотеки DLL установщика
В следующей таблице описаны функции библиотеки DLL установщика. Дополнительные сведения о синтаксисе и семантике каждой функции см. в [справочнике по API DLL установщика](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Задача|Имя функции|Назначение|  
|----------|-------------------|-------------|  
|Установка ODBC|[склконфигдривер](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Загружает библиотеку DLL установки для конкретного драйвера.|  
||[склжетинсталледдриверс](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Возвращает список установленных драйверов.|  
||[склинсталлдриверекс](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Добавляет драйвер в сведения о системе.|  
||[склинсталлдриверманажер](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Возвращает целевой каталог для диспетчера драйверов.|  
||[склинсталлереррор](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Возвращает сведения об ошибке или состоянии для функций установщика.|  
||[склинсталлтранслаторекс](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Добавляет транслятор в сведения о системе.|  
||[склпостинсталлереррор](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Позволяет драйверу или библиотеке установки переводчика сообщать об ошибках.|  
||[склремоведривер](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Удаляет драйвер из сведений о системе.|  
||[склремоведриверманажер](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Удаляет компоненты ODBC Core из сведений о системе.|  
||[склремоветранслатор](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Удаляет транслятор из сведений о системе.|  
|Настройка источников данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Вызывает библиотеку DLL установки для конкретного драйвера.|  
||[склкреатедатасаурце](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Отображает диалоговое окно для добавления источника данных.|  
||[склжетконфигмоде](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Извлекает режим конфигурации, указывающий, где в сведениях о системе отображается запись Odbc.ini с перечнем значений DSN.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Записывает значение в сведения о системе.|  
||[склжеттранслатор](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Отображает диалоговое окно для выбора транслятора.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Отображает диалоговое окно для настройки источников данных и драйверов.|  
||[склреадфиледсн](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Считывает сведения из файлового DSN.|  
||[склремоведефаултдатасаурце](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Удаляет источник данных по умолчанию.|  
||[склремоведснфромини](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Удаляет источник данных.|  
||[склсетконфигмоде](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Задает режим конфигурации, указывающий, где в сведениях о системе отображается запись Odbc.ini с перечнем значений DSN.|  
||[склвалиддсн](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Проверяет длину и допустимость имени источника данных.|  
||[склвритедснтоини](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Добавляет источник данных.|  
||[склвритефиледсн](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Записывает сведения в файловые DSN.|  
||[склвритеприватепрофилестринг](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Возвращает значение из сведений о системе.|
