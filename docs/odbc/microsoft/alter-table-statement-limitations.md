---
title: ALTER TABLE Заявление Ограничения (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19afa8b07b0051de9ce45ec652ea337c0f689f52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304703"
---
# <a name="alter-table-statement-limitations"></a>Ограничения инструкции ALTER TABLE
При использовании драйвера dBASE или Paradox после создания индекса и добавления новой записи структура таблицы не может быть изменена заявлением ALTER TABLE, если индекс не будет удален и содержимое таблицы не удалено.  
  
 Заявления ALTER TABLE не поддерживаются для драйверов Microsoft Excel или Text.  
  
> [!NOTE]  
>  При использовании драйвера Paradox без реализации двигателя базы данных Borland операторы ALTER TABLE не поддерживаются; разрешены только показания по чтению и приложению.
