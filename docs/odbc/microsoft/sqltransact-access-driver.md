---
title: СЗЛТрансакт (Драйвер доступа) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f88d3154925ab589a8519cb9205da03e8c3dc08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299271"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 При использовании драйвера Microsoft Access SQL_COMMIT и SQL_ROLLBACK поддерживаются для аргумента *fType* в вызове в **S'LTransact.**  
  
 При сбое в процессе коммита затронутая база данных может быть восстановлена с помощью опции Repair Database в настройке драйвера Microsoft Access или с помощью REPAIR_DB ключевого слова в функции **S'LConfigDataSource.**
