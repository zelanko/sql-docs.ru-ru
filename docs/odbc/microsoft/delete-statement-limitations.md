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
manager: craigg
ms.openlocfilehash: 98bd56051c724186d7308eff669263d29b82ecd5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198167"
---
# <a name="delete-statement-limitations"></a>Ограничения инструкции DELETE
Инструкции DELETE не поддерживается для драйвера Microsoft Excel или текст. Обратите внимание на то, что драйвер для текстовых поддерживается инструкции INSERT.  
  
 Драйвер для dBASE не поддерживает упаковку таблицу для удаления значений «удалено».  
  
 Для драйвера для Paradox удаление строки из таблицы таблица должна иметь уникальный индекс (первичный ключ для Paradox).
