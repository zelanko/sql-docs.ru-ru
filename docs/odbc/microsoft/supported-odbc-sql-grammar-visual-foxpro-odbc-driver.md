---
title: "Поддерживается SQL-грамматику ODBC (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e5e1755f8c622efceac581e66168666fea9eb86
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Поддерживаемые SQL-грамматику ODBC (драйвер ODBC для Visual FoxPro)
Драйвер ODBC Microsoft Visual FoxPro поддерживает следующие функции:  
  
-   Все инструкции SQL и предложений в минимальную грамматику SQL ODBC  
  
-   Дополнительные инструкции SQL из ядра SQL-грамматику ODBC  
  
 В следующей таблице перечислены элементы, поддерживаемых драйвером по уровню SQL-грамматику ODBC.  
  
|Level|Элементы|Элемент|  
|-----------|--------------|----------|  
|Минимальные|язык описания данных DDL|CREATE TABLE и DROP TABLE|  
||язык обработки данных DML|ВЫБЕРИТЕ, вставки, обновления и удаления|  
||Выражения|Простая (например, объект > B + C)|  
||Типы данных|CHAR, VARCHAR или LONG VARCHAR|  
  
 Помимо поддерживаемых SQL-грамматику ODBC драйвер ODBC для Visual FoxPro поддерживает полный синтаксис собственного языка Visual FoxPro для следующих команд Visual FoxPro.  
  
 [ИНСТРУКЦИЯ ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [УДАЛЕНИЕ ТЕГА](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
