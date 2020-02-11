---
title: SQLProcedures (драйверы баз данных для настольных систем) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLProcedures function [ODBC], Desktop Database Drivers
ms.assetid: c996ad6f-e790-40f4-a962-843422496149
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d778f53f2d82be88aa62489f49712048991b579f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67909962"
---
# <a name="sqlprocedures-desktop-database-drivers"></a>SQLProcedures (драйверы для баз данных на настольном компьютере)
**SQLProcedures** будет возвращать только строки для тех процедур, которые имеют по крайней мере один аргумент. Процедуры, не имеющие аргументов, обрабатываются как представления.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|PROCEDURE_QUALIFIER|Путь к файлу базы данных.|  
|PROCEDURE_OWNER|NULL|  
|PROCEDURE_NAME|Имя процедуры, не разделяются|  
|PROCEDURE_TYPE|SQL_PT_PROCEDURE|
