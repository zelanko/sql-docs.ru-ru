---
description: Загрузка по порядковому номеру
title: Загрузка по порядковому номеру | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb8929962e97e7560f50117218f621cd21846fc4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429636"
---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC *2. x*для повышения производительности процесса подключения можно выполнить загрузку по порядковому номеру. Драйвер ODBC *2. x* экспортирует фиктивную функцию с порядковым номером 199; Когда диспетчер драйверов обнаруживает его, он разрешает адреса функций ODBC по порядковому номеру, а не по имени. Эта функция по-прежнему поддерживается для драйверов ODBC *2. x* , но не поддерживается для драйверов ODBC *3. x* .
