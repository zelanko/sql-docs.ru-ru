---
title: Поддерживаемые грамматики ODBC SQL (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 535f2feaf17d2060c1c65e7aba17951bb3339a5d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080058"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Поддерживаемая грамматика SQL для ODBC (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Microsoft Visual FoxPro поддерживает следующие действия:  
  
-   Все инструкции и предложения SQL в грамматике ODBC минимальная SQL  
  
-   Дополнительная инструкция SQL из грамматики ODBC Core SQL  
  
 В следующей таблице перечислены элементы, поддерживаемые драйвером, по уровню грамматики ODBC SQL.  
  
|Level|Элементы|Элемент|  
|-----------|--------------|----------|  
|Минимальная|Язык описания данных DDL|CREATE TABLE и DROP TABLE|  
||Язык обработки данных DML|ВЫБОР, вставка, обновление и удаление|  
||Выражения|Simple (например,>B + C)|  
||Типы данных|CHAR, VARCHAR или LONG VARCHAR|  
  
 Помимо поддерживаемой грамматики ODBC SQL, драйвер ODBC для Visual FoxPro поддерживает полный собственный синтаксис языка Visual FoxPro для следующих команд Visual FoxPro:  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [УДАЛИТЬ ТЕГ](../../odbc/microsoft/delete-tag-command.md)  
  
 [УДАЛИТЬ ТАБЛИЦУ](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
