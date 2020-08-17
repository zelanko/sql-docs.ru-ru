---
description: Ограничения инструкции DELETE
title: Ограничения инструкции DELETE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5ffb3a6d0ab28fc2b8bc8785df586ac6bbc86aa0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340900"
---
# <a name="delete-statement-limitations"></a>Ограничения инструкции DELETE
Инструкция DELETE не поддерживается для Microsoft Excel или текстового драйвера. Обратите внимание, что инструкция INSERT поддерживается для текстового драйвера.  
  
 Драйвер dBASE не поддерживает упаковку таблиц для удаления "удаленных" значений.  
  
 Чтобы драйвер Paradox удалил строку из таблицы, таблица должна иметь уникальный индекс (первичный ключ Paradox).
