---
title: DLL-файлов установки драйвера | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 851452d2d35e00e1fb39617fc8bfe5c9a5006e68
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="driver-setup-dll"></a>DLL-файлов установки драйвера
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включается в операционной системе Windows. ODBC следует устанавливать только явно на более ранних версиях Windows.  
  
 Настройка драйвера, DLL-Библиотека содержит **ConfigDriver** и **ConfigDSN** функции. **ConfigDriver** задач установки драйвера, например ввода специфические для драйвера информации в реестр. **ConfigDSN** поддерживает специфические для драйвера информацию об источниках данных в реестре. Полное описание этих функций см. в разделе [Справочник по API библиотеки DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** вызывает следующие функции в DLL-ФАЙЛ источника данных в реестре Ведение установщик:  
  
-   **SQLWriteDSNToIni**. Добавление источника данных.  
  
-   **SQLRemoveDSNFromIni**. Удаление источника данных.  
  
-   **SQLWritePrivateProfileString**. Запись значения драйвера подраздела спецификации источника данных.  
  
-   **SQLGetPrivateProfileString**. Чтение значения драйвера из подраздела спецификации источника данных.  
  
-   **SQLGetTranslator**. Запрашивать у пользователя имя переводчик и параметр. Эта функция вызывает **ConfigTranslator** в трансляторе установки библиотеки DLL.  
  
 Настройка драйвера DLL записывается разработчиком драйвера. Он может быть частью драйвера DLL или отдельную библиотеку DLL.
