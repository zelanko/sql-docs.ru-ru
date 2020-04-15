---
title: Функция S'LGetConnectOption (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94a29637365862990ea067f663023fae04a7af3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285574"
---
# <a name="sqlgetconnectoption-function"></a>Функция SQLGetConnectOption
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: Deprecated  
  
 **Сводка**  
 В ODBC *3.x*функция ODBC *2.x* **S'LGetConnectOption** была заменена **на S'LGetConnectAttr**. Для получения более подробной информации, [см.](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
> [!NOTE]
>  Для получения дополнительной информации о том, что менеджер драйвера карты эту функцию, когда приложение ODBC *2.x* работает с драйвером ODBC *3.x,* см. [Отображение раздерок функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении G: Драйвер Руководящие принципы для обратной совместимости.  
> 
> [!NOTE]
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, введенный в ODBC 3.8, не поддерживается **S'LGetConnectOption**. Приложения, которые используют асинхронную операцию на ручке соединения, должны использовать **S'LGetConnectAttr.**  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
