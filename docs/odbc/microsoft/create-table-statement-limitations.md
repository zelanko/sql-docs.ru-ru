---
title: Создание ограничения таблицы инструкция | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7b54b56afb585aa1158394117ebae6cc78116de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899109"
---
# <a name="create-table-statement-limitations"></a>Создание ограничения таблицы инструкция
Если используется Microsoft Access, Microsoft Excel или Paradoxdriver и длина столбца типа text или binary не указан (или указан как 0), будет назначена длина столбца до 255.  
  
 При использовании драйвера dBASE и длина столбца типа text или binary не указан (или указан как 0), будет назначена длина столбца до 254.  
  
 Поддерживается не более 255 столбцов.  
  
 При использовании драйвера Microsoft Excel 97 данных источника, лист или сохраняйте 5.0, 7.0, не может создаваться с тем же именем в виде листа, который ранее был удален. При использовании драйвера Microsoft Excel для доступа к версии 5.0, 7.0 или 97 лист инструкции DROP TABLE удаляет листа, но не удаляет имя листа.  
  
 При использовании драйвера Paradox столбец нельзя добавить после определения индекса для таблицы. Если первый столбец на список аргументов инструкции CREATE TABLE создает индекс, второй столбец нельзя включать в список аргументов.
