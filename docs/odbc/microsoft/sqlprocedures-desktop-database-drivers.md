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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: baad3dc667104000dac9f09e59c12c7670361177
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299454"
---
# <a name="sqlprocedures-desktop-database-drivers"></a>SQLProcedures (драйверы для баз данных на настольном компьютере)
**SQLProcedures** будет возвращать только строки для тех процедур, которые имеют по крайней мере один аргумент. Процедуры, не имеющие аргументов, обрабатываются как представления.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|PROCEDURE_QUALIFIER|Путь к файлу базы данных.|  
|PROCEDURE_OWNER|NULL|  
|PROCEDURE_NAME|Имя процедуры, не разделяются|  
|PROCEDURE_TYPE|SQL_PT_PROCEDURE|
