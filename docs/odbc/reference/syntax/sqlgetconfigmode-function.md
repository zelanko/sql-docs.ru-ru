---
title: Функция Склжетконфигмоде | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc11bec24ede3352dd43f3645fb8c720b77fdabe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285694"
---
# <a name="sqlgetconfigmode-function"></a>Функция SQLGetConfigMode
**Соответствия**  
 Введенная версия: ODBC 3,0  
  
 **Сводка**  
 **Склжетконфигмоде** извлекает режим конфигурации, указывающий, где в сведениях о системе отображается запись ODBC. ini значения DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *пвконфигмоде*  
 Проверки Указатель на буфер, содержащий режим конфигурации. (См. раздел "Комментарии".) Значение в * \*пвконфигмоде* может быть следующим:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, и FALSE в случае сбоя.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склжетконфигмоде** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для определения места, где запись ODBC. ini содержит значения DSN, в сведениях о системе. Если * \*пвконфигмоде* имеет значение ODBC_USER_DSN, то DSN является пользовательским именем DSN, а функция считывает запись из записи ODBC. ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, то DSN является системным именем DSN, а функция считывает из записи ODBC. ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN, HKEY_CURRENT_USER пытается выполнить операцию, а в случае сбоя HKEY_LOCAL_MACHINE используется.  
  
 По умолчанию **склжетконфигмоде** возвращает ODBC_BOTH_DSN. Когда пользовательское имя DSN или системный DSN создается при вызове **SQLConfigDataSource**, функция устанавливает для режима конфигурации значение ODBC_USER_DSN или ODBC_SYSTEM_DSN, чтобы отличать пользовательские и системные имена DSN при изменении имени DSN. Перед возвратом **SQLConfigDataSource** сбрасывает режим конфигурации в ODBC_BOTH_DSN.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка режима конфигурации|[склсетконфигмоде](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
