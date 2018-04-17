---
title: Драйверов на основе файла | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e63c8026b31140f5ad1f94c99f143670d31c5c78
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="file-based-drivers"></a>Драйверов на основе файлов
Драйверов на основе файла используются с источниками данных, например dBASE, не предоставляющих изолированный компонент database engine для использования драйвера. Эти драйверы напрямую обращаться к физических данных и должен реализовывать компонента database engine для обработки инструкций SQL. Стандартная рекомендуется СУБД в драйверов на основе файла реализации подмножество ODBC SQL определяется минимальный уровень совместимости SQL; список инструкций SQL на этом уровне совместимости см. в разделе [грамматику SQL приложение C:](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 В Сравнение файловых и на основе СУБД драйверы драйверов на основе файлов, которые труднее писать из-за компонент ядра СУБД, для настройки, так как нет частей сети проще меньшую мощность потому, что несколько человек времени для записи базы данных модули также производительно, как создаваемые базы данных компании.  
  
 На следующем рисунке две различные конфигурации для драйверов на основе файлов, один, в котором хранятся данные локально, и другой, в котором он находится на сетевом файловом сервере.  
  
 ![Две конфигурации файла&#45;драйверы на основе](../../odbc/reference/media/pr06.gif "pr06")
