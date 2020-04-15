---
title: ЗАЯВЛЕНИЕ CREATE INDEX Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6aa512ff789fcbd00f45f84fb194d4ab3f5da07
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280974"
---
# <a name="create-index-statement"></a>Инструкция CREATE INDEX
Синтаксис оператора CREATE INDEX:  
  
 CREATE (УНИКЕ) *ИНДЕКС-имя* ON *таблицы-имя* *(столб-идентификатор* »ASC » (DESC), *столбец-идентификатор* »ASC »DESC »...) Список \< *опционов* индекса WITH>  
  
 где \< *список опционов индекса*> может быть: PRIMARY &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Только драйвер Microsoft Access использует параметры индекса DISALLOW NULL и IGNORE NULL. Драйверы dBASE и Paradox принимают синтаксис, но игнорируют наличие любого варианта.  
  
 При использовании драйвера Paradox в отчете CREATE INDEX создается основные ключевые файлы парадокса и вторичные файлы.  
  
 Это утверждение не поддерживается драйверами Microsoft Excel или Text.
