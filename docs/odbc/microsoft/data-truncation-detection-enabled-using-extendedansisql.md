---
description: Включение обнаружения усечения данных с использованием ExtendedAnsiSQL
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
ms.openlocfilehash: 26965093caecbc11e94ef738ba6b8ff757b43258
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412895"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Включение обнаружения усечения данных с использованием ExtendedAnsiSQL
Если флаг ExtendedAnsiSQL включен и приложение вставляет данные в символьный или двоичный столбец, а данные усекаются, то усечение будет обнаружено. Если флаг ExtendedAnsiSQL выключен, данные усекаются без предупреждения, как в предыдущих версиях драйверов для базы данных ODBC для настольных систем.
