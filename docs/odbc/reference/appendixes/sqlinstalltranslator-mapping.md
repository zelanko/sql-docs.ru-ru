---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6433df796c88abd7873915266d1a2ca4041a5c62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125728"
---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда приложение ODBC *2. x* вызывает **SQLINSTALLTRANSLATOR** через драйвер ODBC *3. x* , диспетчер драйверов сопоставляет вызов **склинсталлтранслаторекс**. Приложение не должно вызывать **SQLInstallTranslator** в ДИСПЕТЧЕРЕ драйверов ODBC *3. x* с аргументом *лпсзинффиле* , для которого задано значение, отличное от NULL. ODBC. INF-файл, используемый в ODBC *2. x* , больше не поддерживается в ODBC *3. x*, даже для обратной совместимости.
