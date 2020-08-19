---
description: Операции с библиотекой курсоров
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: efe3191e264fe45307ef90624f6b6e76d4ccaff6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429416"
---
# <a name="cursor-library-operations"></a>Операции с библиотекой курсоров
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Если приложение, работающее с драйвером ODBC *2. x* , выполняет вызовы к библиотеке курсоров ODBC *3. x* , приложение может использовать функции ODBC *3. x* , которые не поддерживаются драйвером ODBC *2. x* . Однако разработчик приложения должен быть аккуратным, как именно эти функции используются. Использование библиотеки курсоров ODBC *3. x* не делает драйвер ODBC 2. *x* драйвером ODBC *3. x* .
