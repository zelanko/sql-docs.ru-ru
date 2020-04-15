---
title: Настройка драйвера DLL Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0a2878591c92fe0b2070a295d9dc622c245c17e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306425"
---
# <a name="driver-setup-dll"></a>Библиотека DLL программы установки драйвера
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включен в систему работы Windows. Вы должны только явно установить ODBC на более ранних версиях Windows.  
  
 Установка драйвера DLL содержит функции **ConfigDriver** и **ConfigDSN.** **ConfigDriver** выполняет задачи установки, связанные с драйвером, такие как ввод информации о конкретной информации водителя в реестр. **ConfigDSN** поддерживает в реестре конкретную для водителей информацию об источниках данных. Для полного описания этих [Setup DLL API Reference](../../../odbc/reference/syntax/setup-dll-api-reference.md)функций см.  
  
 **ConfigDSN** вызывает следующие функции в установщике DLL для поддержания информации об источнике данных в реестре:  
  
-   **СЗЛДуНТСНОниИ**. Добавьте источник данных.  
  
-   **СЗЛССНСНИзини**. Удалить источник данных.  
  
-   **СЗЛСРуйтПритПриТпрогвстрст.** Напишите значение конкретного драйвера под подключкой спецификации источника данных.  
  
-   **СЗЛГетПриТпромПрогринг**. Прочитайте значение конкретного драйвера из подключаемого ключа спецификации источника данных.  
  
-   **СЗЛГетПереводчик**. Протяните пользователю имя и опцию переводчика. Эта функция вызывает **ConfigTranslator** в настройке переводчика DLL.  
  
 Настройка драйвера DLL написана разработчиком драйверов. Он может быть частью драйвера DLL или отдельного DLL.
