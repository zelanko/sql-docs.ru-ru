---
title: Индексы dBASE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9db4a41b3f5821fab27c0f779fd4c7cf4d691022
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dbase-indexes"></a>Индексы dBASE
Драйвер ODBC dBASE автоматически открывает и обновляет файлы dBASE IV индекса. Необходимо использовать **Выбор индексов** диалогового окна через администратор источников данных ODBC для связи с файлами dBASE .ndx файлы dBASE III.  
  
 Для создания индексов dBASE применяются следующие ограничения:  
  
-   Все имена столбцов должны быть допустимыми.  
  
-   Все столбцы должны быть в одном по возрастанию или по убыванию.  
  
-   Длина любого отдельного текстового столбца должен быть меньше 100 байт.  
  
-   Если существует более одного столбца, все столбцы должны быть текстовые столбцы, и это сумма размеров столбцов должно быть меньше 100 байт.  
  
-   Невозможно индексировать поля типа MEMO.  
  
-   Индекс не должен быть указан для текущего набора полей (то есть повторяющиеся индексы не допускаются).  
  
-   Имя индекса должно соответствовать соглашению об именах dBASE индекса. dBASE III требует каждого индекса в отдельном файле, каждый из которых .ndx расширения. В dBASE IV индексы создаются как имена тегов, которые хранятся в одном MDX-файла. MDX-файла имеет такое же базовое имя файла базы данных (например, Emp.mdx является индексный файл базы данных Emp.dbf).  
  
-   dBASE определяет уникальный индекс как элемент, где добавляется только одна запись из набора с одинаковыми значениями ключа индекса.
