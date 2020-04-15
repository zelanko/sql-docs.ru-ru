---
title: Функция S'LSetScrollOptions (ru) Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 056fc203581e1d5d8323b09ac62d692093d8c0f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287273"
---
# <a name="sqlsetscrolloptions-function"></a>Функция SQLSetScrollOptions
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: Deprecated  
  
 **Сводка**  
 В ODBC *3.x*функция ODBC 2.0 **S'LSetScrollOptions** была заменена звонками в **S'LGetInfo** и **S'LSetStmtAttr.**  
  
> [!NOTE]
>  Для получения дополнительной информации о том, что менеджер драйвера карты эту функцию, когда приложение ODBC *2.x* работает с драйвером ODBC *3.x,* см. [Отображение раздерок функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении G: Драйвер Руководящие принципы для обратной совместимости.  
> 
> [!NOTE]
>  Когда менеджер драйверов нанесет карты **для** приложения, работающего с драйвером ODBC *3.x,* не поддерживающим **S'LSetScrollOptions,** менеджер-водитель устанавливает опцию SQL_ROWSET_SIZE оператора, а не SQL_ATTR_ROW_ARRAY_SIZE атрибута, *аргументу RowsetSize* в **S'LSetScrollOption.** В результате этого приложение не может использовать сяритогевую опционы **slSetScrollOptions** при получении нескольких строк по вызову в **S'LFetch** или **S'LFetchScroll.** Он может быть использован только при получении нескольких строк по вызову в **S'LExtendedFetch.**  
  
## <a name="remarks"></a>Remarks  
 Если приложение будет работать на 64-битной [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md)операционной системе, см.  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
