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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076114"
---
# <a name="sqlinstalltranslator-function"></a>Функция SQLInstallTranslator
**Соответствия**  
 Введенная версия: ODBC 2,5, не рекомендуется  
  
 **Сводка**  
 В ODBC 3,0 **SQLInstallTranslator** был заменен на [склинсталлтранслаторекс](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Вызовы **SQLInstallTranslator** будут сопоставлены с **склинсталлтранслаторекс**. Дополнительные сведения см. в разделе **склинсталлтранслаторекс**.  
  
 **SQLInstallTranslator** возвращает значение false, если приложение вызывает его в ДИСПЕТЧЕРЕ драйверов ODBC *3. x* с аргументом *лпсзинффиле* , для которого задано значение, отличное от NULL. Файл ODBC. INF, используемый в ODBC *2. x* , больше не поддерживается в ODBC *3. x*, даже для обратной совместимости.
