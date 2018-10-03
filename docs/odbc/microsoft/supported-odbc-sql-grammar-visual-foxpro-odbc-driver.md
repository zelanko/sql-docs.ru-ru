---
title: Поддерживается SQL-грамматику ODBC (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 10df35f4f29de4ac3899efa0e86e48af861f1e65
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751022"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Поддерживаемая грамматика SQL для ODBC (драйвер ODBC для Visual FoxPro)
Драйвер ODBC Microsoft Visual FoxPro поддерживает следующие функции:  
  
-   Все инструкции SQL и предложений в минимальную грамматику SQL ODBC  
  
-   Дополнительные инструкции SQL из ODBC базовую грамматику SQL  
  
 Ниже перечислены элементы, поддерживаемых драйвером, по уровню SQL-грамматику ODBC.  
  
|Level|Элементы|Элемент|  
|-----------|--------------|----------|  
|Минимальные|язык описания данных DDL|CREATE TABLE и DROP TABLE|  
||язык обработки данных DML|Выбор, вставка, обновление и удаление|  
||Выражения|Простое (например, A > B + C)|  
||Типы данных|CHAR, VARCHAR или LONG VARCHAR|  
  
 Помимо поддерживаемых SQL-грамматику ODBC драйвер ODBC для Visual FoxPro поддерживает полный синтаксис собственного языка Visual FoxPro для следующих команд Visual FoxPro:  
  
 [ИНСТРУКЦИЯ ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [УДАЛИТЬ ТЕГ](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
