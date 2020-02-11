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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096311"
---
# <a name="delete-statement-limitations"></a>Ограничения инструкции DELETE
Инструкция DELETE не поддерживается для Microsoft Excel или текстового драйвера. Обратите внимание, что инструкция INSERT поддерживается для текстового драйвера.  
  
 Драйвер dBASE не поддерживает упаковку таблиц для удаления "удаленных" значений.  
  
 Чтобы драйвер Paradox удалил строку из таблицы, таблица должна иметь уникальный индекс (первичный ключ Paradox).
