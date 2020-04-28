---
title: Ограничения инструкции CREATE TABLE | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280875"
---
# <a name="create-table-statement-limitations"></a>Ограничения инструкции CREATE TABLE
Если используется Microsoft Access, Microsoft Excel или Парадоксдривер, а длина текстового или двоичного столбца не указана (или указывается как 0), то длина столбца будет равна 255.  
  
 Если используется драйвер dBASE и длина текстового или двоичного столбца не указана (или указывается как 0), то длина столбца будет равна 254.  
  
 Поддерживается не более 255 столбцов.  
  
 При использовании драйвера Microsoft Excel в источнике данных Микрософтексцел 5,0, 7,0 или 97 лист не может быть создан с тем же именем, что и лист, который ранее был удален. При использовании драйвера Microsoft Excel для доступа к листу версии 5,0, 7,0 или 97 инструкция DROP TABLE очищает лист, но не удаляет имя листа.  
  
 При использовании драйвера Paradox столбцы не могут быть добавлены после определения индекса в таблице. Если первый столбец списка аргументов инструкции CREATE TABLE создает индекс, второй столбец не может быть добавлен в список аргументов.
