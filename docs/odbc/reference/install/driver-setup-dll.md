---
title: Библиотека DLL настройки драйвера | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094165"
---
# <a name="driver-setup-dll"></a>Библиотека DLL программы установки драйвера
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Библиотека DLL установки драйвера содержит функции **конфигдривер** и **ConfigDSN** . **Конфигдривер** выполняет специфические для драйвера задачи установки, такие как ввод в реестр сведений, относящихся к драйверу. **ConfigDSN** хранит сведения об источниках данных, относящиеся к драйверу, в реестре. Полное описание этих функций см. в [справочнике по API DLL установки](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** вызывает следующие функции в библиотеке DLL установщика для сохранения сведений об источнике данных в реестре:  
  
-   **Склвритедснтоини**. Добавьте источник данных.  
  
-   **Склремоведснфромини**. Удаление источника данных.  
  
-   **Склвритеприватепрофилестринг**. Запишите значение, зависящее от драйвера, в подразделе спецификации источника данных.  
  
-   **SQLGetPrivateProfileString**. Считывание значения, зависящего от драйвера, из подраздела спецификации источника данных.  
  
-   **Склжеттранслатор**. Запрашивать у пользователя имя и параметр переводчика. Эта функция вызывает **конфигтранслатор** в библиотеке DLL установки транслятора.  
  
 Библиотека DLL установки драйвера написана разработчиком драйвера. Он может быть частью библиотеки DLL драйвера или отдельной библиотекой DLL.
