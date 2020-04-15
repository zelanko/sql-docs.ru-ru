---
title: Функция S'LInstallTranslator Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b094aa730fff6db80b9addb63a92bee0f5f85b2a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300324"
---
# <a name="sqlinstalltranslator-function"></a>Функция SQLInstallTranslator
**Соответствия**  
 Версия Введена: ODBC 2.5, Обезображенный  
  
 **Сводка**  
 В ODBC 3.0, **S'LInstallTranslator** был заменен [на S'LInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Вызовы на **S'LInstallTranslator** будут отображены на **sLInstallTranslatorEx**. Для получения более подробной информации, **см.**  
  
 **S'LInstallTranslator** вернет FALSE, если приложение вызывает его в ODBC *3.x* Менеджер драйвера с *lpszInfFile* аргумент установлен на значение, кроме NULL. Файл Odbc.inf, используемый в ODBC *2.x,* больше не поддерживается в ODBC *3.x,* даже для обратной совместимости.
