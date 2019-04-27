---
title: Включено с использованием ExtendedAnsiSQL Включение обнаружения усечения данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95b7d538c2ace45b42c947b56ca5a5bd5f981ec5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62744277"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включение обнаружения усечения данных с использованием ExtendedAnsiSQL
Если включен флаг ExtendedAnsiSQL и приложение осуществляет вставку данных в char или двоичным столбцом, и данные будут усечены, обнаруживается усечение. Если флаг ExtendedAnsiSQL отключено, данные усекаются без предупреждения, как это было в предыдущих версиях драйверов ODBC базы данных.
