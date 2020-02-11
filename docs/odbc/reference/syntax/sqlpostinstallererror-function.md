---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d5e0a10b8c530494fa3c026be0d36fde066a97c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053669"
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
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS или SQL_ERROR.  
  
## <a name="diagnostics"></a>Диагностика  
 **Склпостинсталлереррор** не помещать значения ошибок для самого себя. Если ошибка была успешно отправлена в очередь ошибок установщика (которую можно получить с помощью **склинсталлереррор**), возвращается SQL_SUCCESS. SQL_ERROR возвращается, если значение аргумента *дверроркоде* не является одним из указанных кодов ошибок установщика.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[конфигдривер](../../../odbc/reference/syntax/configdriver-function.md)|  
|Добавление, изменение и удаление источников данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Задание параметра перевода|[конфигтранслатор](../../../odbc/reference/syntax/configtranslator-function.md)|
