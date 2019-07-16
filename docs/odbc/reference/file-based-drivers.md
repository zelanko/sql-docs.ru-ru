---
title: Драйверы на основе файла | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 803da51c8507faa47f92b295d3749f00317bc413
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915386"
---
# <a name="file-based-drivers"></a>Драйверы на основе файлов
Драйверы на основе файла используются с источниками данных, например dBASE, которые не предоставляют изолированный компонент database engine для использования драйвера. Эти драйверы прямой доступ к физических данных и должен реализовывать компонента database engine для обработки инструкций SQL. Обычной практикой ядра СУБД в драйверы на основе файла реализует подмножество ODBC SQL, определяется минимальный уровень соответствия SQL; список инструкций SQL на этом уровне совместимости, см. в разделе [приложение в: Грамматика SQL](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 В Сравнение файловых и на основе СУБД драйверы драйверы на основе файла являются труднее писать, из-за компонент ядра базы данных, проще настроить, так как нет частей сети и менее мощных потому, что немногие времени для записи базы данных модули мощные, как создаваемые базы данных компании.  
  
 Ниже показан две различные конфигурации для драйверов на основе файла: один, в котором данные хранятся локально, а другая в которой она находится на сетевом файловом сервере.  
  
 ![Две конфигурации файла&#45;драйверы на основе](../../odbc/reference/media/pr06.gif "pr06")
