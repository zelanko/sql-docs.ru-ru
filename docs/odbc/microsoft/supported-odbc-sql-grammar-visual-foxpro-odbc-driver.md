---
title: Поддерживаемая грамматика ODBC S'L (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f72548d0708a63f887f7d6da4d4f5988500f0eef
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304087"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Поддерживаемая грамматика SQL для ODBC (драйвер ODBC для Visual FoxPro)
Microsoft Visual FoxPro ODBC Драйвер поддерживает следующее:  
  
-   Все заявления и положения в грамматике ODBC с минимальным уровнем S'L  
  
-   Еще одно заявление с s'L из грамматики ODBC core S'L  
  
 В следующей таблице перечислены элементы, поддерживаемые драйвером, по уровню грамматики ODBC S'L.  
  
|Level|Элементы|Item|  
|-----------|--------------|----------|  
|Минимальные|язык описания данных DDL|CREATE TABLE и DROP TABLE|  
||язык обработки данных DML|СЕЛЕКТ, ВСТАВКА, ОБНОВЛЕНИЕ и DELETE|  
||Выражения|Просто (например, A>B'C)|  
||Типы данных|CHAR, VARCHAR, или LONG VARCHAR|  
  
 В дополнение к поддерживаемой грамматике ODBC S'L, Visual FoxPro ODBC Driver поддерживает полный родной визуальный синтаксис языка FoxPro для следующих команд Visual FoxPro:  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [СОЗДАТЬ ТАБЛИЦУ](../../odbc/microsoft/create-table-sql-command.md)  
  
 [Удалить](../../odbc/microsoft/delete-sql-command.md)  
  
 [УДАЛИТЬ ТЕГ](../../odbc/microsoft/delete-tag-command.md)  
  
 [ТАБЛИЦА СБРОСА](../../odbc/microsoft/drop-table-command.md)  
  
 [Индекс](../../odbc/microsoft/index-command.md)  
  
 [Вставить](../../odbc/microsoft/insert-sql-command.md)  
  
 [Выберите](../../odbc/microsoft/select-sql-command.md)  
  
 [Обновление](../../odbc/microsoft/update-sql-command.md)
