---
description: Сопоставление SQLInstallTranslator
title: Сопоставление SQLInstallTranslator | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fc571e305070e4afba6dc7c647d18a6790c011f0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448973"
---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда приложение ODBC *2. x* вызывает **SQLINSTALLTRANSLATOR** через драйвер ODBC *3. x* , диспетчер драйверов сопоставляет вызов **склинсталлтранслаторекс**. Приложение не должно вызывать **SQLInstallTranslator** в ДИСПЕТЧЕРЕ драйверов ODBC *3. x* с аргументом *лпсзинффиле* , для которого задано значение, отличное от NULL. ODBC. INF-файл, используемый в ODBC *2. x* , больше не поддерживается в ODBC *3. x*, даже для обратной совместимости.
