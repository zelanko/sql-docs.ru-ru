---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eb2587f733f5042436144f7865627fee576e3d9c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096311"
---
# <a name="delete-statement-limitations"></a>Ограничения инструкции DELETE
Инструкции DELETE не поддерживается для драйвера Microsoft Excel или текст. Обратите внимание на то, что драйвер для текстовых поддерживается инструкции INSERT.  
  
 Драйвер для dBASE не поддерживает упаковку таблицу для удаления значений «удалено».  
  
 Для драйвера для Paradox удаление строки из таблицы таблица должна иметь уникальный индекс (первичный ключ для Paradox).
