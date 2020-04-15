---
title: Компоненты установки Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a196e9b935229fa03c6dd0eda92b8e99e69f0ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285254"
---
# <a name="installation-components"></a>Компоненты установки
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC включен в систему работы Windows. Вы должны только явно установить ODBC на более ранних версиях Windows.  
  
 Процесс установки начинается, когда пользователь запускает программу настройки. Программа настройки работает в сочетании с *установщиком DLL* и *установкой драйвера DLL* для каждого водителя. Как программа настройки, так и установщик DLL используют аргументы в функциях **S'LInstallDriverDriverEx** и **S'LInstallTranslatorEx,** чтобы определить, какие файлы копировать или удалять для каждого компонента. Следующая иллюстрация показывает взаимосвязь между этими компонентами установки.  
  
 ![Связь между компонентами установки](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Файл Odbc.inf, который использовался в ODBC *2.x* для описания файлов, требуемых каждым компонентом ODBC, не используется в ODBC *3.x*. Драйверы, которые подают компоненты ODBC *3.x,* не должны создавать файл Odbc.inf. Удаление **S'LInstallDriver** и **S'LInstallODBC**, и амортизацию **S'LInstallTranslator**, сделали Odbc.inf ненужным. Информация о драйверах, которая раньше была в разделах ключевых слов драйверов Odbc.inf, теперь содержится в аргументе *lpszDriver* в **sLInstallDriverEx.** Информация переводчика, которая раньше была в разделах «Переводчик ODBC» и спецификации переводчика Odbc.inf, теперь представлена в аргументе *lpszTranslator* of **s'LInstallTranslatorEx**. Эти изменения позволяют ODBC Installer быть более портативными на разных платформах.  
  
 Для получения дополнительной информации об этих компонентах смотрите следующие темы в конце этого раздела.  
  
-   [Программа установки](../../../odbc/reference/install/setup-program.md)  
  
-   [Библиотека DLL установщика](../../../odbc/reference/install/installer-dll.md)  
  
-   [Библиотека DLL программы установки драйвера](../../../odbc/reference/install/driver-setup-dll.md)
