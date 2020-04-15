---
title: СЗЛУстановитьПереводчик Картирование (ru) Документы Майкрософт
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
ms.openlocfilehash: 8ab5ebccaac7ccf6374971c1d21040ad15fb3e55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300586"
---
# <a name="sqlinstalltranslator-mapping"></a>Сопоставление SQLInstallTranslator
Когда приложение ODBC *2.x* вызывает **S'LInstallTranslator** через драйвер ODBC *3.x,* менеджер драйвера драйвера водителя отображает вызов на **S'LInstallTranslatorEx.** Приложение не должно вызывать **S'LInstallTranslator** в МЕНЕДЖЕРе драйверов ODBC *3.x* с аргументом *lpszInfFile,* установленным на значение, не являвщееся NULL. The ODBC. Файл INF, используемый в ODBC *2.x,* больше не поддерживается в ODBC *3.x,* даже для обратной совместимости.
