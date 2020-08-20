---
description: Функция SQLGetConfigMode
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
ms.openlocfilehash: 75093ddb5b33427ac2dc86c3d31fa635a2899118
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491249"
---
# <a name="sqlgetconfigmode-function"></a>Функция SQLGetConfigMode
**Соответствия**  
 Введенная версия: ODBC 3,0  
  
 **Сводка**  
 **Склжетконфигмоде** извлекает режим конфигурации, указывающий, где Odbc.ini записи в список значений DSN находятся в системной информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *пвконфигмоде*  
 Проверки Указатель на буфер, содержащий режим конфигурации. (См. раздел "Комментарии".) Значение в * \* пвконфигмоде* может быть следующим:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Возвращаемое значение  
 Функция возвращает TRUE, если она успешна, и FALSE в случае сбоя.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склжетконфигмоде** возвращает значение false, связанное значение * \* пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \* пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для определения того, где в сведениях о системе находится запись Odbc.ini, в которой перечислены значения DSN. Если * \* пвконфигмоде* имеет значение ODBC_USER_DSN, то DSN является пользовательским именем DSN, а функция считывает из записи Odbc.ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, то DSN является системным именем DSN, а функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN, HKEY_CURRENT_USER пытается выполнить операцию, а в случае сбоя HKEY_LOCAL_MACHINE используется.  
  
 По умолчанию **склжетконфигмоде** возвращает ODBC_BOTH_DSN. Когда пользовательское имя DSN или системный DSN создается при вызове **SQLConfigDataSource**, функция устанавливает для режима конфигурации значение ODBC_USER_DSN или ODBC_SYSTEM_DSN, чтобы отличать пользовательские и системные имена DSN при изменении имени DSN. Перед возвратом **SQLConfigDataSource** сбрасывает режим конфигурации в ODBC_BOTH_DSN.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка режима конфигурации|[склсетконфигмоде](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
