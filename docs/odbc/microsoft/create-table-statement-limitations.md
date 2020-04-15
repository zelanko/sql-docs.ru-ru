---
title: CREATE TABLE Заявление Ограничения (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a83acb061cf8192dff1c6adede349f49a0b0bbdb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280875"
---
# <a name="create-table-statement-limitations"></a>Ограничения инструкции CREATE TABLE
При использовании Microsoft Access, Microsoft Excel или Paradoxdriver и длины текста или двоичного столбца не указывается (или указана как 0), длина столбца будет установлена до 255.  
  
 Когда используется драйвер dBASE и длина текста или двоичной колонки не указана (или указана как 0), длина столбца будет установлена до 254.  
  
 Поддерживается максимум 255 столбцов.  
  
 Когда драйвер Microsoft Excel используется на MicrosoftExcel 5.0, 7.0 или 97 источнике данных, лист не может быть создан с тем же именем, что и лист, который ранее был удален. Когда драйвер Microsoft Excel используется для доступа к версии 5.0, 7.0 или 97 листа, заявление DROP TABLE очищает лист, но не удаляет имя листа.  
  
 При использовании драйвера Парадокс атакжем не может быть добавлен, как только индекс определен на столе. Если первый столбец списка аргументов оператора CREATE TABLE создает индекс, второй столбец не может быть включен в список аргументов.
