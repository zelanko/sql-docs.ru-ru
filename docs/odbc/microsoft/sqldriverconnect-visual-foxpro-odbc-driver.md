---
title: SLDriverConnect (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e270f8c9be42dc109adeaa49acb84f29f2b9511
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307095"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Подключается к существующему источнику данных, который может быть либо [базой данных,](../../odbc/microsoft/visual-foxpro-terminology.md) либо каталогом [свободных таблиц.](../../odbc/microsoft/visual-foxpro-terminology.md) Ключевые слова атрибута ODBC UID и PWD игнорируются. В следующей таблице перечислены дополнительные ключевые слова поддерживаемого атрибута.  
  
|Ключевое слово атрибута ODBC|Значение атрибута|  
|----------------------------|---------------------|  
|DSN||  
|ИД пользователя|Игнорируется Visual FoxPro ODBC Driver, но не генерирует ошибку.|  
|PWD|Игнорируется Visual FoxPro ODBC Driver, но не генерирует ошибку.|  
|Драйвер|Название и местоположение визуального драйвера FoxPro ODBC; реализовано менеджером драйвера.|  
  
|Визуальный FoxPro ODBC Драйвер атрибут ключевое слово|Значение атрибута|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Да" или "Нет"|  
|Разобрать по копиям|"Машина" или другая последовательность сопоставления. Список поддерживаемых последовательностей сопоставления см. [SET COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Описание||  
|Монопольная блокировка|"Да" или "Нет"|  
|SourceDB|Полностью квалифицированный путь к каталогу, содержащий ноль или более [свободных таблиц,](../../odbc/microsoft/visual-foxpro-terminology.md)или абсолютный путь и имя файла для [базы данных.](../../odbc/microsoft/visual-foxpro-terminology.md)|  
|Тип источника|"DBC" или "DBF"|  
|Version||  
  
 Если имя источника данных не указано, менеджер драйвера подсказывает пользователю информацию (в зависимости от настройки аргумента *fDriverCompletion),* а затем продолжает. Если требуется дополнительная информация, драйвер Visual FoxPro ODBC отображает оперативный диалог.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)
