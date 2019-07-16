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
ms.openlocfilehash: ad141939a548aa008ef7109d0adaec5b3a8c6c3d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002006"
---
# <a name="cursor-library-operations"></a>Операции с библиотекой курсоров
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 Если приложение, работа с ODBC *2.x* драйвер выполняет вызовы ODBC *3.x* библиотека курсоров, приложение может иметь возможность использовать ODBC *3.x* функций, которые не являются поддерживаемый ODBC *2.x* драйвера. Разработчику приложения следует соблюдать осторожность, как эти функции используются, однако. Использование ODBC *3.x* библиотека курсоров не выполняет ODBC *2.x* драйвера в ODBC *3.x* драйвера.
