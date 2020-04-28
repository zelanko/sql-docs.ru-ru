---
title: Обнаружение усечения данных включено с помощью ExtendedAnsiSQL | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae1aa7a8a8b9ea2c3f3054717546506e660d5270
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280704"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включение обнаружения усечения данных с использованием ExtendedAnsiSQL
Если флаг ExtendedAnsiSQL включен и приложение вставляет данные в символьный или двоичный столбец, а данные усекаются, то усечение будет обнаружено. Если флаг ExtendedAnsiSQL выключен, данные усекаются без предупреждения, как в предыдущих версиях драйверов для базы данных ODBC для настольных систем.
