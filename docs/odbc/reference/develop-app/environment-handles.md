---
title: Обработки окружающей среды Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b504995e99dfad032598485e370b4d5a6681ae81
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300444"
---
# <a name="environment-handles"></a>Дескрипторы среды
*Среда* — это глобальный контекст, в котором можно получить доступ к данным; связанной с окружающей средой любая информация, которая имеет глобальный характер, например:  
  
-   Состояние окружающей среды  
  
-   Текущая диагностика на уровне окружающей среды  
  
-   Ручки соединений, в настоящее время выделенных на окружающую среду  
  
-   Текущие параметры атрибута каждой среды  
  
 В части кода, реализуемого ODBC (менеджер драйвера или драйвера), ручка среды определяет структуру, содержащую эту информацию.  
  
 Ручки среды не часто используются в приложениях ODBC. Они всегда используются в вызовах на веб-ссылки **ИК-ЛДСИ-Драйверы,** а иногда и в вызовах на вызовы в **S'LAllocHandle,** **S'LEndTran**, **S'LFreeHandle**, **S'LGetDiagField**, и **SQLDataSources** **S'LGetDiagRec**.  
  
 Каждый фрагмент кода, который реализует ODBC (менеджер драйвера или драйвер) содержит одну или несколько декейок среды. Например, менеджер драйвера поддерживает отдельную ручку среды для каждого приложения, подключенного к нему. Ручки среды распределяются с **помощью S'LAllocHandle** и освобождаются с **помощью S'LFreeHandle.**
