---
title: Примечания к реализации (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 970188a2fca45706405e398cece0f04d38dfdc68
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284316"
---
# <a name="implementation-notes"></a>Примечания по реализации
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 В этом разделе описывается, как реализуется библиотека курсоров ODBC. В нем описывается, как библиотека курсора поддерживает свой кэш, выполняет операторы S'L и реализует функции ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Кэш библиотеки курсоров](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [Обработка инструкций SQL](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [Функции ODBC и библиотека курсоров](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
