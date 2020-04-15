---
title: Delete Заявление Ограничения Документы Майкрософт
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
ms.openlocfilehash: 365b54ab8c0678253e184b397f1f71e39aed3b9b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303535"
---
# <a name="delete-statement-limitations"></a>Ограничения инструкции DELETE
Заявление DELETE не поддерживается для драйвера Microsoft Excel или Text. Обратите внимание, что заявление INSERT поддерживается для драйвера текста.  
  
 Драйвер dBASE не поддерживает упаковку таблицы для удаления "удаленных" значений.  
  
 Для того чтобы драйвер Paradox удалил строку из таблицы, таблица должна иметь уникальный индекс (основной ключ Парадокса).
