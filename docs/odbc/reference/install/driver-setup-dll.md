---
title: Библиотека DLL программы установки драйвера | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df91638f91091940e00e7a6a19d0fd6cb700f85f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094165"
---
# <a name="driver-setup-dll"></a>Библиотека DLL программы установки драйвера
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включена в операционную систему Windows. ODBC следует только явным образом установить в более ранних версиях Windows.  
  
 Настройка драйвера, библиотека DLL содержит **ConfigDriver** и **ConfigDSN** функции. **ConfigDriver** задач установки конкретного драйвера, например ввод данных специфические для драйвера в реестре. **ConfigDSN** хранит сведения об источниках данных в реестре. Полное описание этих функций, см. в разделе [Справочник по API библиотеки DLL программы установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** вызывает следующие функции в программе установки, чтобы обеспечить источника данных в реестре:  
  
-   **SQLWriteDSNToIni**. Добавьте источник данных.  
  
-   **SQLRemoveDSNFromIni**. Удаление источника данных.  
  
-   **SQLWritePrivateProfileString**. Запись значения специфические для драйвера подключе спецификации источника данных.  
  
-   **SQLGetPrivateProfileString**. Чтение значения специфические для драйвера из подраздела спецификации источника данных.  
  
-   **SQLGetTranslator**. Приглашение ввести имя translator и параметр. Эта функция вызывает **ConfigTranslator** в трансляторе библиотеки DLL программы установки.  
  
 Настройка драйвера DLL записывается разработчиком драйвера. Он может быть частью драйвера библиотеки DLL или отдельный файл DLL.
