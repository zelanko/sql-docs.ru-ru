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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5eab1c3bf6891f10c897966035dced2ffdc10ba
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232208"
---
# <a name="create-table-statement-limitations"></a>Ограничения инструкции CREATE TABLE
Если используется Microsoft Access, Microsoft Excel или Paradoxdriver и длина столбца типа text или binary не указан (или равен 0), длина столбца будет указано значение 255.  
  
 Если используется драйвер для dBASE и длина столбца типа text или binary не указан (или равен 0), длина столбца будет присвоено 254.  
  
 Поддерживается более 255 столбцов.  
  
 При использовании драйвера Microsoft Excel 97 данных источника, лист или сохраняйте 5.0, 7.0, не может создаваться с тем же именем в виде листа, который ранее был удален. При использовании драйвера Microsoft Excel для доступа к версии 5.0, 7.0 или 97 лист инструкции DROP TABLE удаляет рабочего листа, но не удаляйте имя листа.  
  
 Если используется драйвер для Paradox, столбцы нельзя добавить после определения индекса для таблицы. Если в первом столбце списка аргументов инструкции CREATE TABLE создает индекс, второй столбец не может использоваться в списке аргументов.
