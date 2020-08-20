---
description: Функция SQLPostInstallerError
title: Функция Склпостинсталлереррор | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a041069de4c8b86946f7088d6a46462468cc3656
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487213"
---
# <a name="sqlpostinstallererror-function"></a>Функция SQLPostInstallerError
**Соответствия**  
 Введенная версия: ODBC 3,0  
  
 **Сводка**  
 **Склпостинсталлереррор** предоставляет механизм для драйвера или библиотеки установки переводчика, сообщающий об ошибках функций **конфигдривер**, **ConfigDSN**и **конфигтранслатор** в очередь ошибок установщика. Приложения не используют этот API; они используют **склинсталлереррор** для получения ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ферроркоде*  
 Входной Код ошибки установщика.  
  
 *сзеррормсг*  
 Входной Текст сообщения об ошибке.  
  
## <a name="returns"></a>Возвращаемое значение  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **Склпостинсталлереррор** не помещать значения ошибок для самого себя. Если ошибка была успешно отправлена в очередь ошибок установщика (которую можно получить с помощью **склинсталлереррор**), возвращается SQL_SUCCESS. SQL_ERROR возвращается, если значение аргумента *дверроркоде* не является одним из указанных кодов ошибок установщика.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[конфигдривер](../../../odbc/reference/syntax/configdriver-function.md)|  
|Добавление, изменение и удаление источников данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Задание параметра перевода|[конфигтранслатор](../../../odbc/reference/syntax/configtranslator-function.md)|
