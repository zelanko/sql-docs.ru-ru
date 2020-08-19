---
description: SQLProcedures (драйверы для баз данных на настольном компьютере)
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
ms.openlocfilehash: 86e24f0b077816dab1ca75f939d6bb8456a948ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483337"
---
# <a name="sqlprocedures-desktop-database-drivers"></a>SQLProcedures (драйверы для баз данных на настольном компьютере)
**SQLProcedures** будет возвращать только строки для тех процедур, которые имеют по крайней мере один аргумент. Процедуры, не имеющие аргументов, обрабатываются как представления.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|PROCEDURE_QUALIFIER|Путь к файлу базы данных.|  
|PROCEDURE_OWNER|NULL|  
|PROCEDURE_NAME|Имя процедуры, не разделяются|  
|PROCEDURE_TYPE|SQL_PT_PROCEDURE|
