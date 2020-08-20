---
description: Поддерживаемая грамматика SQL для ODBC (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3057520e5aca5277a68971513ef28427f27208ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471506"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Поддерживаемая грамматика SQL для ODBC (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Microsoft Visual FoxPro поддерживает следующие действия:  
  
-   Все инструкции и предложения SQL в грамматике ODBC минимальная SQL  
  
-   Дополнительная инструкция SQL из грамматики ODBC Core SQL  
  
 В следующей таблице перечислены элементы, поддерживаемые драйвером, по уровню грамматики ODBC SQL.  
  
|Level|Элементы|Элемент|  
|-----------|--------------|----------|  
|Минимальные|язык описания данных DDL|CREATE TABLE и DROP TABLE|  
||язык обработки данных DML|ВЫБОР, вставка, обновление и удаление|  
||Выражения|Simple (например,>B + C)|  
||Типы данных|CHAR, VARCHAR или LONG VARCHAR|  
  
 Помимо поддерживаемой грамматики ODBC SQL, драйвер ODBC для Visual FoxPro поддерживает полный собственный синтаксис языка Visual FoxPro для следующих команд Visual FoxPro:  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [УДАЛИТЬ ТЕГ](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [НОМЕР](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
