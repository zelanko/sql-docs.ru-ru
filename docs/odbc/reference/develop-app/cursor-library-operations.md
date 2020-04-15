---
title: Операции библиотеки Cursor (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2297e72aacad7ea91b7af934a47bebbc61f0686
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301621"
---
# <a name="cursor-library-operations"></a>Операции с библиотекой курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Если приложение, работая с драйвером ODBC *2.x,* делает звонки в библиотеку курсоров ODBC *3.x,* приложение может использовать функции ODBC *3.x,* которые не поддерживаются драйвером ODBC *2.x.* Однако автор приложений должен быть осторожен в использовании этих функций. Использование библиотеки курсоров ODBC *3.x* не делает драйвер ODBC *2.x* драйвером ODBC *3.x.*
