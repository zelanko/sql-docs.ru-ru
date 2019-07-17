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
ms.openlocfilehash: d7fb67171a796755bf8d6229b9d562f69bd588ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096509"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включение обнаружения усечения данных с использованием ExtendedAnsiSQL
Если включен флаг ExtendedAnsiSQL и приложение осуществляет вставку данных в char или двоичным столбцом, и данные будут усечены, обнаруживается усечение. Если флаг ExtendedAnsiSQL отключено, данные усекаются без предупреждения, как это было в предыдущих версиях драйверов ODBC базы данных.
