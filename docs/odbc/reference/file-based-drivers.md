---
title: Драйверы на основе файлов | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 223bd838754f1d656ac71ae37926389097af3ea1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306667"
---
# <a name="file-based-drivers"></a>Драйверы на основе файлов
Драйверы на основе файлов используются с такими источниками данных, как dBASE, которые не предоставляют автономное ядро СУБД для использования драйвером. Эти драйверы напрямую обращаются к физическим данным и должны реализовать ядро СУБД для обработки инструкций SQL. В качестве стандартной практики ядра СУБД в драйверах на основе файлов реализуют подмножество ODBC SQL, определяемое минимальным уровнем соответствия SQL. список инструкций SQL на этом уровне соответствия см. в [приложении C: грамматика SQL](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 При сравнении драйверов на основе файлов и СУБД файловые драйверы сложнее писать из-за компонента ядра СУБД, менее сложены в настройке из-за отсутствия компонентов сети и менее мощными, так как некоторые люди имеют время на написание ядер баз данных как мощных в компаниях баз данных.  
  
 На следующем рисунке показаны две различные конфигурации драйверов на основе файлов, один из которых располагает данными локально, а другой — в сетевом файловом сервере.  
  
 ![Две конфигурации драйверов на основе файлов&#45;](../../odbc/reference/media/pr06.gif "pr06")
