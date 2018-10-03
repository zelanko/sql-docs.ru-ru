---
title: Операции с библиотекой курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32e3fcaf9c83c2613a1dc2df499f11c7df2570ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692402"
---
# <a name="cursor-library-operations"></a>Операции с библиотекой курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Если приложение, работа с ODBC 2 *.x* драйвер выполняет вызовы ODBC 3. *x* библиотека курсоров, приложение может иметь возможность использовать ODBC 3. *x* функции, которые не поддерживаются в ODBC 2 *.x* драйвера. Разработчику приложения следует соблюдать осторожность, как эти функции используются, однако. Использование ODBC 3. *x* библиотека курсоров не выполняет ODBC 2 *.x* драйвера в ODBC 3. *x* драйвера.
