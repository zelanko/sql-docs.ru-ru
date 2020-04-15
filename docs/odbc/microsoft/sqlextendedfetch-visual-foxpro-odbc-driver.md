---
title: S'LExtendedFetch (Визуальный водитель FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ecff538198a2b517f980cc63acfc97d29a9f162
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298654"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: Уровень 2  
  
 Подобно [S'LFetch,](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) но возвращает несколько строк, используя массив для каждого столбца. Набор результатов является прокруткой вперед и может быть сделан назад-прокрутки, если курсор определяется как статический, а не только вперед.  
  
 По умолчанию Visual FoxPro ODBC Driver не возвращает строки, помеченные как удаленные в таблице FoxPro. Строки, помеченные для удаления, но еще не удаленные из таблицы, не включены в курсор набора результатов. Вы можете изменить это поведение с помощью команды [SET DELETED.](../../odbc/microsoft/set-deleted-command.md)  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md)
