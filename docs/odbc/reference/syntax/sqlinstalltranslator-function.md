---
title: Функция SQLInstallTranslator | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5b973332c2fe0fa541635d326a3a5adecf6ae91
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076114"
---
# <a name="sqlinstalltranslator-function"></a>Функция SQLInstallTranslator
**Соответствие стандартам**  
 Представленные версии: 2.5, рекомендуется использовать ODBC  
  
 **Сводка**  
 В ODBC 3.0 **SQLInstallTranslator** был заменен классом [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Вызовы **SQLInstallTranslator** будут сопоставлены с **SQLInstallTranslatorEx**. Дополнительные сведения см. в разделе **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** вернет FALSE, если приложение вызывает его в ODBC *3.x* диспетчера драйверов с *lpszInfFile* аргументу присвоено значение, отличное от NULL. Файл Odbc.inf, используемый в ODBC *2.x* больше не поддерживается в ODBC *3.x*, даже если для обеспечения обратной совместимости.
