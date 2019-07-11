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
manager: craigg
ms.openlocfilehash: 50bfa00f482110d3d0695ef249e8758b5db02c80
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792815"
---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда ODBC *2.x* приложение вызывает **SQLInstallTranslator** через ODBC *3.x* драйвера, диспетчер драйверов сопоставляет вызов  **SQLInstallTranslatorEx**. Приложение не должно вызывать **SQLInstallTranslator** в ODBC *3.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. ODBC. INF-файл, используемый в ODBC *2.x* больше не поддерживается в ODBC *3.x*, даже если для обеспечения обратной совместимости.
